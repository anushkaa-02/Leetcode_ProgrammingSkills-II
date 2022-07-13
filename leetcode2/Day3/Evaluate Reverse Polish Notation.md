# Evaluate Reverse Polish Notation
- ## Question:
>Evaluate the value of an arithmetic expression in Reverse Polish Notation.
>
>Valid operators are +, -, *, and /. Each operand may be an integer or another expression.
>
>Note that division between two integers should truncate toward zero.
>
>It is guaranteed that the given RPN expression is always valid. That means the expression would always evaluate to a result, and there will not be any division by >zero operation.

- Example :

      Input: tokens = ["2","1","+","3","*"]
      Output: 9
      Explanation: ((2 + 1) * 3) = 9
      
- ## Solution:
```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int>st;
        for(auto x: tokens){
            if(x=="+"||x=="-"||x=="*"||x=="/"){
                int op2=st.top();
                st.pop();
                int op1=st.top();
                st.pop();
                if(x=="+"){
                    st.push(op1+op2);
                }
                if(x=="-"){
                    st.push(op1-op2);
                }
                if(x=="*"){
                    st.push(op1*op2);
                }
                if(x=="/"){
                    st.push(op1/op2);
                }
            }
            else
            {
                stringstream ss(x);
                int data;
                ss>>data;
                st.push(data);
            }
        }
        return st.top();
    }
};
```

## Tags
`Array` `Math` `Stack`
