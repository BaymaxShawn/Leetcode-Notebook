# 😎 2469 - Convert the Temperature

You are given a non-negative floating point number rounded to two decimal places `celsius`, that denotes the **temperature in Celsius**.

You should convert Celsius into **Kelvin** and **Fahrenheit** and return it as an array `ans = [kelvin, fahrenheit]`.

Return _the array `ans`._ Answers within `10-5` of the actual answer will be accepted.

**Note that:**

* `Kelvin = Celsius + 273.15`
* `Fahrenheit = Celsius * 1.80 + 32.00`

&#x20;

**Example 1:**

<pre><code><strong>Input: celsius = 36.50
</strong><strong>Output: [309.65000,97.70000]
</strong><strong>Explanation: Temperature at 36.50 Celsius converted in Kelvin is 309.65 and converted in Fahrenheit is 97.70.
</strong></code></pre>

**Example 2:**

<pre><code><strong>Input: celsius = 122.11
</strong><strong>Output: [395.26000,251.79800]
</strong><strong>Explanation: Temperature at 122.11 Celsius converted in Kelvin is 395.26 and converted in Fahrenheit is 251.798.
</strong></code></pre>

&#x20;

**Constraints:**

* `0 <= celsius <= 1000`

## Solution

```python
class Solution:
    def convertTemperature(self, celsius: float) -> List[float]:

        return [celsius+273.15,celsius * 1.80 + 32.00]
```

