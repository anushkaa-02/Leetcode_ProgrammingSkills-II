# Group Anagrams
- ## Question:
>Given an array of strings strs, group the anagrams together. You can return the answer in any order.
>
>An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

- Example :

      Input: strs = ["eat","tea","tan","ate","nat","bat"]
      Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
      
- ## Solution:
```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        std::map<std::string, std::vector<std::string>> anagrams;
        std::string tmp;
        for (auto const &str : strs) {
            tmp = str;
            std::sort(tmp.begin(), tmp.end());
            anagrams[tmp].push_back(str);
        }
        std::vector<std::vector<std::string>> result;
        for (auto &[_, vec] : anagrams) {
            result.push_back(std::move(vec));
        }
        return result;
    }
};
```

## Tags
`Array` `HashTable` `String`
