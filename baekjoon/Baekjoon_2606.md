# [BaekJoon#2606] 바이러스  



> ### Problem
>
> https://www.acmicpc.net/problem/2606



> ### Solution
>
> 1. union-find

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    static int[] computer;
    static int[] parent;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());
        int union = Integer.parseInt(br.readLine());

        computer = new int[N+1];
        parent = new int[N+1];
        // 초기화
        for(int i=1; i<=N; i++){
            computer[i] = parent[i] = i;
        }

        StringTokenizer token;
        
        while(union-->0){
            token = new StringTokenizer(br.readLine(), " ");
            unionParent(Integer.parseInt(token.nextToken()), Integer.parseInt(token.nextToken()));
        }

        int count = 0;     // 1번 자신 제외

        for (int i=2; i<parent.length; i++){
            if(parent[i] == 1) count++;
        }
        System.out.println(count);
    }

    public static void unionParent(int com1, int com2){
        int x = getParent(com1);
        int y = getParent(com2);
        if(x < y){
            // 연결되어있는 컴퓨터들 모두 최상위 부모 교체
            for(int i=2; i< parent.length; i++){
                if(parent[i] == y){
                    parent[i] = x;
                }
            }
        } else {
            // 연결되어있는 컴퓨터들 모두 최상위 부모 교체
            for(int i=2; i< parent.length; i++){
                if(parent[i] == x){
                    parent[i] = y;
                }
            }
        }
    }
    public static int getParent(int i){
        if(parent[i] == i) return i;
        return parent[i] = getParent(parent[i]);
    }
}
```

| 참고 반례                       |
| ------------------------------- |
| 5<br/>3<br/>1 2<br/>3 4<br/>2 4 |



> 2. graph

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.StringTokenizer;

public class Main {
	public static void main(String[] args) throws NumberFormatException, IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int num = Integer.parseInt(br.readLine());
		int edge = Integer.parseInt(br.readLine());
		
		Graph graph = new Graph(num);
		while(edge-->0) {
			StringTokenizer token = new StringTokenizer(br.readLine(), " ");
			graph.addEdge(Integer.parseInt(token.nextToken()), Integer.parseInt(token.nextToken()));
		}
		
		int count = graph.countVirus(1);
		System.out.println(count);
	}
}
class Graph {
	private Node[] nodeArr;
	class Node {
		int data;				// 정점의 데이터 값
		LinkedList<Node> adj;	// 인접 정점 리스트
		boolean visited;
		
		public Node(int data){
			this.data = data;
			this.adj = new LinkedList<Node>();
			this.visited = false;
		}
	}
	public Graph(int size){
		this.nodeArr = new Node[size+1];
		for(int i=1; i<=size; i++) {
			nodeArr[i] = new Node(i);
		}
	}
	public void addEdge(int node1, int node2) {
		Node no1 = nodeArr[node1];
		Node no2 = nodeArr[node2];
		
		if(!no1.adj.contains(no2)) {
			no1.adj.add(no2);
		}
		if(!no2.adj.contains(no1)) {
			no2.adj.add(no1);
		}
	}
	public int countVirus(int i) {
		int count = 0;
		Node node = nodeArr[i];
		node.visited = true;
		for(Node n : node.adj) {
			if(!n.visited) {
				count ++;
				count += countVirus(n.data);
			}
		}
		return count;
	}
}

```