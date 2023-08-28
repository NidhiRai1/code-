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


//SCC(stronglly connected component) BY KOSRAJU'S ALGORITHUM
*it help in finding the stronglly connected component in the directed graph
*Within every scc each node are rechable
*in this algorithum reversed visiting of node can be done so that we can't do the whole traversal in the ehtire tree

----sort all the node according to their finishing time do the topological sort .tc O(n)  sc 
-----do the transpose of graph (change the direction of graph) . tc = O(n + e)
----again od the dfs call store the count of each scc node. tc = O(n + e)

we need stack + visited arry + transpose graph = o(n) + o(n) + o(n+e)


class Solution
{
private:
    void dfs(int node, vector<int> &vis, vector<int> adj[],
             stack<int> &st) {
        vis[node] = 1;
        for (auto it : adj[node]) {
            if (!vis[it]) {
                dfs(it, vis, adj, st);
            }
        }

        st.push(node);
    }
private:
    void dfs3(int node, vector<int> &vis, vector<int> adjT[]) {
        vis[node] = 1;
        for (auto it : adjT[node]) {
            if (!vis[it]) {
                dfs3(it, vis, adjT);
            }
        }
    }
public:
    //Function to find number of strongly connected components in the graph. this is topological sort
    int kosaraju(int V, vector<int> adj[])
    {
        vector<int> vis(V, 0);
        stack<int> st;
        for (int i = 0; i < V; i++) {
            if (!vis[i]) {
                dfs(i, vis, adj, st);
            }
        }
//transformation the direction
        vector<int> adjT[V];
        for (int i = 0; i < V; i++) {
            vis[i] = 0;
            for (auto it : adj[i]) {
                // i -> it
                // it -> i
                adjT[it].push_back(i);
            }
        }
    //count the scc nodes
        int scc = 0;
        while (!st.empty()) {
            int node = st.top();
            st.pop();
            if (!vis[node]) {
                scc++;
                dfs3(node, vis, adjT);
            }
        }
        return scc;
    }
}:
