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