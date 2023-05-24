package BFSAndDFS;
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;

class Graph
{
	ArrayList<ArrayList<Integer>>graph= new ArrayList<ArrayList<Integer>>();
	int v;
	
	Graph(int node)
	{
		v=node;
//		graph = new ArrayList<ArrayList<Integer>>();
		
		for(int i=0;i<v;i++)
		{
			graph.add( new ArrayList<Integer>());
		}
	}
	
	void addEdge(int v,int u)
	{
		graph.get(v).add(u);
		graph.get(u).add(v);
	}
	
	void printGraph()
	{
		for(int i=0;i<v;i++)
		{
			System.out.println("Node " + i);
			
			for(int x: graph.get(i))
			{
				System.out.println("-> "+x);
			}
		}
	}
	
	void bsf(int start)
	{
		boolean visited[] = new boolean[v];
		System.out.println("BSF travesal");
		Queue<Integer>q = new LinkedList<Integer>();
		q.add(start);
		visited[start] = true;
		
		while(q.isEmpty()==false)
		{
			int node = q.poll();
			
			System.out.print(node+" ");
			
			for(int x: graph.get(node))
			{
				if(visited[x] ==false)
				{
					visited[x]=true;
					q.add(x);
				}
			}
			
		}
		
	}
}
public class bfs {

	public static void main(String[] args) {
		
		Graph g = new Graph(5);
		g.addEdge(0, 1);
		g.addEdge(3, 2);
		g.addEdge(1, 4);
		g.addEdge(3, 2);
		g.addEdge(0, 4);
		
		g.printGraph();
		
		g.bsf(0);

	}

}
