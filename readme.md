# StatQueue (formerly MedianQueue)

A streaming data structure that supports FIFO operations while maintaining real-time statistical metrics.

Unlike traditional approaches that compute statistics separately, StatQueue maintains:

- Median
- Mode
- Mean
- Min / Max
- Sum

…all together in a single unified structure.

---

## ⚡ Why this exists

In streaming / sliding window problems, computing statistics typically requires:

- Heaps for median (complex rebalancing)
- Hash maps for mode (extra tracking)
- Full traversal for mean/sum

StatQueue combines all of these into one structure with:

- O(log n) updates  
- O(1) queries  
- FIFO removal support  

---

## 🧠 Core Idea

StatQueue combines:

- **Ordered structure (multiset)** → median, min, max  
- **Frequency buckets** → mode  
- **Running sum** → mean  
- **Deque (FIFO)** → sliding window  

All structures stay synchronized on every insert/pop.

---

## 🧩 Internal Architecture

            +-------------------+
            |      Deque        |
            |   (FIFO order)    |
            +---------+---------+
                      |
                      v
    +----------------------------------+
    |          Multiset (BST)          |
    |  Sorted order of elements        |
    |  ↑ median pointer maintained     |
    +----------------------------------+
         |        |           |
         v        v           v
       Min      Median       Max

    +-----------------------------+
    |     Frequency Map           |
    |     value → frequency       |
    +-------------+---------------+
                  |
                  v
    +-----------------------------+
    |   Frequency Buckets         |
    | freq → set of values        |
    | (for O(1) mode retrieval)   |
    +-----------------------------+

    +-----------------------------+
    |        Running Sum          |
    |   used for mean calculation |
    +-----------------------------+


---

## ⏱ Complexity

| Operation     | Time Complexity |
|--------------|----------------|
| insert(x)     | O(log n)       |
| pop()         | O(log n)       |
| getMedian()   | O(1)           |
| getMode()     | O(1)           |
| getMean()     | O(1)           |
| getMin/Max()  | O(1)           |
| getSum()      | O(1)           |

---

## 🔍 Comparison

| Feature        | Heaps | Multiset | StatQueue |
|---------------|------|----------|----------|
| Median        | ✅   | ✅       | ✅       |
| Mode          | ❌   | ❌       | ✅       |
| Mean / Sum    | ❌   | ❌       | ✅       |
| Min / Max     | ❌   | ✅       | ✅       |
| FIFO support  | ❌   | ❌       | ✅       |
| Unified DS    | ❌   | ❌       | ✅       |

---

## 📖 Usage Example

```cpp
#include "MedianQueue.h"
#include <iostream>

int main() {
    MedianQueue mq;
    mq.insert(5);
    mq.insert(2);
    mq.insert(8);

    std::cout << "Median: " << mq.getMedian() << std::endl;
    std::cout << "Mean: " << mq.getMean() << std::endl;
    std::cout << "Mode: " << mq.getMod() << std::endl;
    std::cout << "Min: " << mq.getMin() << std::endl;
    std::cout << "Max: " << mq.getMax() << std::endl;
    std::cout << "Sum: " << mq.getSum() << std::endl;

    mq.pop();

    std::cout << "\nAfter popping one element:" << std::endl;
    std::cout << "Median: " << mq.getMedian() << std::endl;

    return 0;
}
```
   
## 📌 Applications

- Real-time analytics with sliding windows
- Signal & data stream processing
- Competitive programming utilities
- Systems requiring fast statistical summaries

---

## 🏷️ License & Credits

**Author:** Shashank Vashistha  
**Copyright:** Registered (Diary No. SW-30440/2025-CO)  
Open for academic and educational use.

---

## ⭐ If you find this project useful, consider giving it a star on GitHub!
