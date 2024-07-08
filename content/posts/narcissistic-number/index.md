---
title: 'Narcissistic Number 水仙花數'
date: 2022-11-09T14:59:43+08:00
draft: false
tags:
  - algorithm
  - c++
summary: '尋找 0 至 1000 的 Narcissistic Number 並使迴圈在 200 次以內結束'
cover:
  image: 'cover.png'
  caption: ''
  alt: 'Narcissistic Number Example'
  relative: true
---
## 題目內容
尋找 `0` 至 `1000` 的 Narcissistic Number 並使迴圈在 200 次以內結束。

## 程式碼
```cpp
#include <iostream>

using namespace std;

int main() {
    int mp[1000] = {0};
    int count = 0;
    for(int i = 0; i < 10; i++) {
        count++;
        cout << i << endl;
        int n = i*i*i - i;
        mp[n] = i;
    }

    for(int i = 1; i < 10; i++) {
        for(int k = 0; k < 10; k++) {
            count++;
            // Second Digit Check
            if((i*i + k*k) == (i * 10 + k)) {
                cout << i << k << endl;
            }

            // Third Digit Check
            int n = i * 100 + k * 10 - i*i*i - k*k*k;
            if(n == 0) {
                cout << i << k << 0 << endl;
                cout << i << k << 1 << endl;
            } else if(n > 0) {
                if(mp[n] != 0) {
                    cout << i << k << mp[n] << endl;
                }
            }
        }
    }
    cout << "Count: " << count << endl;
    return 0;
}
```