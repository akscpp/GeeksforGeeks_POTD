[Problem Link](https://www.geeksforgeeks.org/problems/account-merge/1)<br>
Given a list of accounts of size n where each element accounts [ i ] is a list of strings, where the first element account [ i ][ 0 ]  is a name, and the rest of the elements are emails representing emails of the account.
Geek wants you to merge these accounts. Two accounts belong to the same person if there is some common email to both accounts. Note that even if two accounts have the same name, they may belong to different people as people could have the same name. A person can have any number of accounts initially, but all of their accounts have the same name.
After merging the accounts, return the accounts in the following format: The first element of each account is the name, and the rest of the elements are emails in sorted order.

Note: Accounts themselves can be returned in any order.<br>

Example 1:<br>

Input:
n = 4<br>
accounts [ ] =<br>
[["John","johnsmith@mail.com","john_newyork@mail.com"],<br>
["John","johnsmith@mail.com","john00@mail.com"],<br>
["Mary","mary@mail.com"],<br>
["John","johnnybravo@mail.com"]]<br>
Output:<br>
[["John","john00@mail.com","john_newyork@mail.com", "johnsmith@mail.com"],<br>
["Mary","mary@mail.com"],<br>
["John","johnnybravo@mail.com"]]<br>
Explanation:
The first and second John's are the same person as they have the common email "johnsmith@mail.com". The third John and Mary are different people as none of their email addresses are used by other accounts.We could return these arrays in any order, for example, the answer [['Mary', 'mary@mail.com'], ['John', 'johnnybravo@mail.com'], ['John', 'john00@mail.com', 'john_newyork@mail.com', 'johnsmith@mail.com']] would still be accepted.<br>
Example 2:<br>

Input:
n = 5<br>
accounts [ ] =<br>
[["Gabe","Gabe00@m.co","Gabe3@m.co","Gabe1@m.co"],<br>
["Kevin","Kevin3@m.co","Kevin5@m.co","Kevin0@m.co"],<br>
["Ethan","Ethan5@m.co","Ethan4@m.co","Ethan0@m.co"],<br>
["Hanzo","Hanzo3@m.co","Hanzo1@m.co","Hanzo0@m.co"],<br>
["Fern","Fern5@m.co","Fern1@m.co","Fern0@m.co"]]<br>
Output:<br>
[["Ethan","Ethan0@m.co","Ethan4@m.co","Ethan5@m.co"],<br>
["Gabe","Gabe0@m.co","Gabe1@m.co","Gabe3@m.co"],<br>
["Hanzo","Hanzo0@m.co","Hanzo1@m.co","Hanzo3@m.co"],<br>
["Kevin","Kevin0@m.co","Kevin3@m.co","Kevin5@m.co"],<br>
["Fern","Fern0@m.co","Fern1@m.co","Fern5@m.co"]]<br>
Explanation:
We don't have any common emails in any of the users. We just sorted the emails of each person and we return a array of emails.(The details can be returned in any order).<br>
Your Task:
You don't need to read or print anything. Your task is to complete the function accountsMerge() which takes a list of lists of strings representing accounts[][] as a parameter and returns a list of lists of strings denoting the details after merging.<br>

Expected Time Complexity: O(n*m*logn) - where n is the size of accounts and m is the size of the number of strings for a name.<br>
Expected Auxiliary Space: O(n*m) - where n is the size of accounts and m is the size of the number of strings for a name.<br>

Constraints:<br>
1 <= n <= 1000<br>
2 <= accounts[ i ].size <= 10<br>
1 <= accounts[ i ][ j ].size <= 30<br>
accounts[i][0] consists of English letters.<br>

__Intuition ->The code initially assigns each email account its own parent, tracks the account owners, and later updates the parent relationship to ensure all emails belonging to the same person share the same root parent. By grouping emails under their root parents, it effectively merges accounts, resulting in a final list where each entry represents a merged account with all associated emails and their owner.__

```C++
string find(string s , map<string,string>&p){
        if(p[s]==s){
            return s;
        }
        return find(p[s],p);
    }
    vector<vector<string>> accountsMerge(vector<vector<string>> &accounts) {
        // code here
        map<string,string>owner;
        map<string,string>parent;
        map<string,set<string>>unions;
        
        for(int i=0;i<accounts.size();i++){
            for(int j=1;j<accounts[i].size();j++){
                parent[accounts[i][j]]=accounts[i][j];
                owner[accounts[i][j]]=accounts[i][0];
            }
        }
        
        for(int i=0;i<accounts.size();i++){
            string p = find(accounts[i][1],parent);
            
            for(int j=2;j<accounts[i].size();j++){
                parent[find(accounts[i][j],parent)]=p;
            }
        }
        
        
        for(int i=0;i<accounts.size();i++){
            for(int j=1;j<accounts[i].size();j++){
                unions[find(accounts[i][j],parent)].insert(accounts[i][j]);
            }
        }
        
        vector<vector<string>>ans;
        
        for(pair<string,set<string>>p : unions){
            vector<string>res(p.second.begin(),p.second.end());
            res.insert(res.begin(),owner[p.first]);
            ans.push_back(res);
        }
        
        return ans;
        
    }
```
