# code-\

//DFS - firstly go to the left most of the graph then right most atlest in one idrection first 

we need - visited arry = so that we not regoing to the same path 
adj matrix = store the nebhour 
starting node = 0 
and a vector ot store the end result 

first function call second function and in that recurssion goes on

private:
    void dfs(int start , vector<int> adj[] , vector<int> &is , int vlsi[] ){
        vlsi[start] = 1 ;
        is.push_back(start);
        
        for(auto it : adj[start]){
            if(!vlsi[it]){
                dfs(it , adj ,is , vlsi);
            }
        }
    }
  public:
    // Function to return a list containing the DFS traversal of the graph.
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
     int  vlsi[V] = {0};
     int start = 0;
     vector<int> is ;
     dfs(start , adj , is , vlsi);
    }
):

//bfs - it travers levle wise 

same four variable needed visited array , node = 0 , , queue , adjency matrix , vector to store the result

class Solution {
  public:
    // Function to return Breadth First Traversal of given graph.
    vector<int> bfsOfGraph(int V, vector<int> adj[]) {
        int vis[V] = {0}; 
        vis[0] = 1; 
        queue<int> q;
        // push the initial starting node 
        q.push(0); 
        vector<int> bfs; 
        // iterate till the queue is empty 
        while(!q.empty()) {
           // get the topmost element in the queue 
            int node = q.front(); 
            q.pop(); 
            bfs.push_back(node); 
            // traverse for all its neighbours 
            for(auto it : adj[node]) {
                // if the neighbour has previously not been visited, 
                // store in Q and mark as visited 
                if(!vis[it]) {
                    vis[it] = 1; 
                    q.push(it);  
                }
            }
        }
        return bfs; 
    }
};

//DETECT A CYCLE IN A UNPAIRDER GRAPH (BFS)
basic way is that we need to have a pair of queue to store the  <source , parant node> 
if at any point of time we get the same source node but different parant node then that means taht it is cyclic 
bool cycle( int V  , vector<int> adj){
vlsi [V] = {0} ;
queue<pair<int ,int >> q ;
q.push(0 , -1);
while(!q.empty()){
int SN = q.front().first ; 
q.pop.first ;
int PN = q.front().second ;
q.pop.second;

for(auto it : adj[SN]){
if(! vlsi[]{
q.push(it ,SN);
}
else if(it != PN){
return true ;
}
}}
retrurn false ;
}
} :
