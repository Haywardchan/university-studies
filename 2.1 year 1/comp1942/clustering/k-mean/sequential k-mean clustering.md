1. inclement n whenever a new data point x is out
2. replace old mean $m_i$ by $\frac{1}{n_i}(x-m_i)$

general form
$$m_i(t)=m_i(t-1)+\frac{1}{t}(x_t-m_i(t-1))$$
refer the proof on goodnotes

advantages:
1. acquire the examples over a period of time, we can start the clustering before seeing all the examples
2. quick execution