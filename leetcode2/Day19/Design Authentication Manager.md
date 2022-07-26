# Design Authentication Manager
- ## Question:
>There is an authentication system that works with authentication tokens. For each session, the user will receive a new authentication token that will expire >timeToLive seconds after the currentTime. If the token is renewed, the expiry time will be extended to expire timeToLive seconds after the (potentially different) >currentTime.
>
>Implement the AuthenticationManager class:

- AuthenticationManager(int timeToLive) constructs the AuthenticationManager and sets the timeToLive.
- generate(string tokenId, int currentTime) generates a new token with the given tokenId at the given currentTime in seconds.
- renew(string tokenId, int currentTime) renews the unexpired token with the given tokenId at the given currentTime in seconds. If there are no unexpired tokens with the given tokenId, the request is ignored, and nothing happens.
- countUnexpiredTokens(int currentTime) returns the number of unexpired tokens at the given currentTime.

- Example :

      Input
      ["AuthenticationManager", "renew", "generate", "countUnexpiredTokens", "generate", "renew", "renew", "countUnexpiredTokens"]
      [[5], ["aaa", 1], ["aaa", 2], [6], ["bbb", 7], ["aaa", 8], ["bbb", 10], [15]]
      Output
      [null, null, null, 1, null, null, null, 0]
      
- ## Solution:
```cpp
class AuthenticationManager {
    int livingTime;
    unordered_map<string, int> cache; //<id, endTime>
public:
    AuthenticationManager(int timeToLive) {
        livingTime=timeToLive;
        cache={};
    }
    
    void generate(string tokenId, int currentTime) {
        cache[tokenId]=currentTime+livingTime;
    }
    
    void renew(string tokenId, int currentTime) {
        if(cache.count(tokenId) && cache[tokenId]>currentTime)
            cache[tokenId]=currentTime+livingTime;
    }
    
    int countUnexpiredTokens(int currentTime) {
        int count=0;
        for(auto &[id, time]: cache)
            if(currentTime<time)
                count++;
        return count;
    }
};
```

## Tags
`Hash Table` `Design`
