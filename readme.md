# MedianQueue

A novel data structure that extends the capabilities of a standard queue by enabling O(1) retrieval of statistical measures such as median, mean, mode, min, max, and sum within a sliding window.

This project is implemented in C++ and registered under Copyright (Diary No. SW-30440/2025-CO).

## 🚀 Features

- Queue operations (insert, pop, peek)
- Constant-time access to:
  - Median
  - Mean
  - Mode
  - Min / Max
  - Sum
- Sliding window support (automatically maintains order with pop())
- Fully self-contained, STL-based implementation
- Resettable state with `dumpState()`

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

    mq.pop(); // Removes the oldest element (5)
    
    std::cout << "\nAfter popping one element:" << std::endl;
    std::cout << "Median: " << mq.getMedian() << std::endl; // Now median of {2, 8} is 2
    
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
Open for academic and educational.

---

## ⭐ If you find this project useful, consider giving it a star on GitHub!
