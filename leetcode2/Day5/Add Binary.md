# Add Binary
- ## Question:
>Given two binary strings a and b, return their sum as a binary string.

- Example :

      Input: a = "1010", b = "1011"
      Output: "10101"
      
- ## Solution:
```cpp
class Solution {
public:
    string addBinary(string a, string b) {
		string result;
		
		int i = a.length()-1,j = b.length()-1;
		int carry = 0;
		
		while(i >= 0 || j >= 0){
			int sum = carry;
			if(i >= 0) sum += a[i--] - '0';
			if(j >= 0) sum += b[j--] - '0';

			carry = sum > 1 ? 1 : 0;
			result += to_string(sum%2);
		}
		
		if(carry) result += to_string(carry);
		reverse(result.begin(),result.end());
		
		return result;
    }
};
```

## Tags
`Math` `String` `Bit manipulation`
