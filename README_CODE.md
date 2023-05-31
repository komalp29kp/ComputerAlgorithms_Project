In this project, I used Dev C++ application to run the code.
Code:
#include<bits/stdc++.h>
 
using namespace std;
 
int j,i,e,n;
vector<vector<int> > graph;
vector<int> color;
bool vis[100011];
 
void greedyColoring()
{
    color[0]  = 0;
    for (i=1;i<n;i++)
        color[i] = -1;
 
    bool unused[n];
 
    for (i=0;i<n;i++)
        unused[i]=0;
 
 
    for (i = 1; i < n; i++)
    {
        for (j=0;j<graph[i].size();j++)
            if (color[graph[i][j]] != -1)
                unused[color[graph[i][j]]] = true;
        int a;
        for (a=0;a<n;a++)
            if (unused[a] == false)
                break;
 
        color[i] = a; 
 
        for (j=0;j<graph[i].size();j++)
            if (color[graph[i][j]] != -1)
                unused[color[graph[i][j]]] = false;
    }
}
 
int main()
{
    int x,y;
    cout<<"please enter total number of vertices and edges:";
    cin>>n>>e;
    cout<<"\n";
    graph.resize(n);
    color.resize(n);
    memset(vis,0,sizeof(vis));
    for(i=0;i<e;i++)
    {
        cout<<"\nEnter edge vertices of edge "<<i+1<<" :";
        cin>>x>>y;
        x--; y--;
        graph[x].push_back(y);
        graph[y].push_back(x);
    }
    greedyColoring();
    for(i=0;i<n;i++)
    {
        cout<<"Vertex "<<i+1<<" is coloured  "<<color[i]+1<<"\n";
    }
}

RESULT:

After running the code in Dev c++ application, Need to enter the inputs. For instance, I haD 
taken the inputs as follows: 
Total number of edges and vertices: 4 5
enter edge vertices of edge 1: 1 2
enter edge vertices of edge 2: 2 3
enter edge vertices of edge 3: 3 4
enter edge vertices of edge 4: 4 1
enter edge vertices of edge 5: 2 4

The results obtained is:
Vertex 1 is coloured with 1st color.
Vertex 2 is coloured with 2nd color.
Vertex 3 is coloured with 1st color.
Vertex 4 is coloured with 3rd color.

