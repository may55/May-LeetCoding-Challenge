#   Implement Trie (Prefix Tree)

Implement a trie with insert, search, and startsWith methods.

### Example 1:

    Trie trie = new Trie();
    trie.insert("apple");
    trie.search("apple");   // returns true
    trie.search("app");     // returns false
    trie.startsWith("app"); // returns true
    trie.insert("app");   
    trie.search("app");     // returns true

## Explanation

1. Simple Trie

## Code:

```
class Trie {
public:    
    Trie *next[26];
    bool isEnd = false;
    /** Initialize your data structure here. */
    Trie() {
        memset(next,NULL,sizeof(next));
    }
    
    /** Inserts a word into the trie. */
    void insert(string word) {
        Trie *t = this;
        for(char ch: word){
            if(!t->next[ch-'a'])
                t->next[ch-'a'] = new Trie();
            t = t->next[ch-'a'];
        }
        t->isEnd = true;
    }
    
    /** Returns if the word is in the trie. */
    bool search(string word) {
        Trie *t = this;
        for(char ch: word){
            if(!t->next[ch-'a'])
                return false;
            t = t->next[ch-'a'];
        }
        return t->isEnd;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string word) {
        Trie *t = this;
        for(char ch: word){
            if(!t->next[ch-'a'])
                return false;
            t = t->next[ch-'a'];
        }
        return true;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```
