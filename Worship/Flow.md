一生的恩惠
約書亞
遮蓋我
Cathay
Heihei74
https://www.cloudskillsboost.google/journeys/118


Given:
enum Tree[K, V] extends TreeInterface[K, V]:
  private case Leaf(key: K, payload: V)
  private case Node(key: K, children: List[Tree[K, V]])
  import Tree.Path
and the interface as :
package ass1
trait TreeInterface[K, V]:
  import Tree.Path
  def key: K
  def contains(path: Path[K]): Boolean
  def get(path: Path[K]): Option[Either[List[K], V]]
  def flatten: List[(Path[K], V)]
  def updated(path: Path[K]): Tree[K, V]
  def updated(path: Path[K], payload: V): Tree[K, V]
trait TreeComp:
  def apply[K, V](key: K): Tree[K, V]
  def apply[K, V](path: Path[K]): Tree[K, V]
  def apply[K, V](path: Path[K], payload: V): Tree[K, V]
  case class Path[K](segs: List[K])
  object IllegalPathException extends java.lang.Exception





def updated(path: Path[K], payload: V): Tree[K, V] =

    if path.segs.isEmpty || path.segs.head!=this.key

    then throw Tree.IllegalPathException

    else

      this match

        case Node(key, children) => path.segs match

          case x::Nil =>

            //drop the children with same key no matter is leaf or node

            val updatedchild = children.dropWhile(x==_.key):+Leaf(key, payload)

            Node(key, updatedchild)

          case xs =>

            if xs.head!=key then

              val updatedchild = children :+ Node(xs.head, Nil).updated(Path(xs.tail), payload)

              Node(key, updatedchild)

            else

              children.find(_.key == xs.head) match {

                case Some(child) =>

                  val updatedChild = child.updated(Path(xs.tail), payload)

                  Node(key, children.map(c => if (c.key == xs.head) updatedChild else c))

                case None =>

                  Node(key, children :+ Node(xs.head, Nil).updated(Path(xs.tail), payload))}

        case Leaf(key, payload) => Leaf(key, payload)//updates cover in case Node




```
def apply[K, V](path: Path[K], payload: V): Tree[K, V] = path match

    case Path(Nil) => throw IllegalPathException

    case _ =>

      def listToNode[K](list: List[K]): Tree[K, V] = {

        list.foldRight[Tree[K, V]](Leaf(list.last, payload)) {

          case (item, acc) => Node(item, List(acc))

        }

      }

      listToNode(path.segs)
```