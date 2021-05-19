# permutation
C++:
class Solution {
public:
    vector<vector<int> > permute(vector<int> &num) {
        // Start typing your C/C++ solution below
        // DO NOT write int main() function
        if(num.size()<=0) return vector<vector<int>>();
        sort(num.begin(),num.end());
        vector<vector<int>> result;
        vector<int>res;
        vector<bool> used(num.size(),false);
        dfs(result,res,num,used,num.size());
        return result;
    }
    void dfs(vector<vector<int>> &result,vector<int> &res,vector<int> num,vector<bool> &used,int n){
    
        if(n==0){
            result.push_back(res);
            return;
        }
        for(int i=0;i<num.size();i++){
            if(used[i]==false){
                used[i]=true;
                res.push_back(num[i]);
                dfs(result,res,num,used,n-1);
                res.pop_back();
                used[i]=false;
            }
        }
    }
};
Java:
public class Solution {
    public ArrayList<ArrayList<Integer>> permute(int[] num) {
        // Start typing your Java solution below
        // DO NOT write main() function
        ArrayList<ArrayList<Integer>> result=new ArrayList<ArrayList<Integer>>();
        if(num==null||num.length<=0) return result;
        ArrayList<Integer> res=new ArrayList<Integer>();
        boolean[] used=new boolean[num.length];
        for(int i=0;i<used.length;i++) used[i]=false;
        dfs(result,res,num,used,num.length);
        return result;
    }
    public void dfs(ArrayList<ArrayList<Integer>> result,ArrayList<Integer> res,int[] num,boolean[] used,int n){
        if(n==0){
            ArrayList<Integer> cur=new ArrayList<Integer>();
            for(int i=0;i<res.size();i++) cur.add(res.get(i));
            result.add(cur);
            return;
        }
        for(int i=0;i<used.length;i++){
            if(used[i]==false){
                used[i]=true;
                res.add(num[i]);
                dfs(result,res,num,used,n-1);
                res.remove(res.size()-1);
                used[i]=false;
            }
        }
    }
}
