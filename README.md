# 01-BFS-leetcode-Minimum-Cost-to-Make-at-Least-One-Valid-Path-in-a-Grid-

class Solution {
public:
    int minCost(vector<vector<int>>& grid) {
        int n=grid.size();
        int m=grid[0].size();
        vector<vector<int>>change(n,vector<int>(m,INT_MAX));
        change[0][0]=0;
        vector<pair<int,int>>dir={{0,1},{0,-1},{1,0},{-1,0}};
        queue<pair<int,int>>q;
        q.push({0,0});
        while(!q.empty()){
           auto[x,y]=q.front();
            q.pop();
            
            for(auto k=0;k<4;k++){
                int childx=dir[k].first+x;
                int childy=dir[k].second+y;
                if(childx<0||childy<0||childx>=n||childy>=m) continue;
                if(grid[x][y]==k+1){
                if(change[childx][childy]>change[x][y]){
                 change[childx][childy]=change[x][y];
                    q.push({childx,childy});
                }
                    
                }else if(change[childx][childy]>change[x][y]+1){
                    change[childx][childy]=change[x][y]+1;
                    q.push({childx,childy});
                }
                
            }
            }
            
        
        
        
        return change[n-1][m-1];
        
        
    }
};
