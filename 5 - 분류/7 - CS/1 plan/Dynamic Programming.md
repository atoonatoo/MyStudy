
---
- [[CS]]
---
### 다이나믹 프로그래밍
- 다이나믹 프로그래밍의 탄생 계기
	- 다이나믹 프로그래밍은 완전 탐색 , DFS, BFS와 같이 수많은 경우에 수를 따져봐야하는데 그 경우의 수가 너무 많아서 속도가 느려지는 것을 개선하고자, 수행 시간을 단축하고자 만들어진 알고리즘이다.
	
- 다이나믹 프로그래밍의 목적
	- **메모리를 사용해서 중복 연산을 줄이고 중복 연산을 줄여서 수행 속도를 개선한다.**
	- 메모리를 사용한다. -> 배열 혹은 자료구조를 만든다.
	- 중복연산을 줄인다. -> 연산한 결과를 배열에 담는다.
	
- 정수 삼각형 문제
	- 핵심
		- DP 삼각형을 어떻게 정의하고, 값을 차곡차곡 쌓아서 중복 연산을 줄이느냐.
	
- 왜 이걸 다이나믹 프로그래밍이라고 불리는 이유
	- 기억하기 알고리즘
	- 기억하며 알고리즘
	- 연산한 내용을 기억하고, 기억한 값을 사용해서 문제를 푸는게 다이나믹프로그래밍의 전부
	  
- 구분법
	- 다양한 유형의 문제를 최적화 할 때 고려될 수 있는 알고리즘이다.
	- 코딩 테스트, 알고리즘 문제에서 이건 DP로 풀어야겠다고 판단할 수 있는 기준
		1. DFS/BFS로 풀 수는 있지만, 경우의 수가 너무 많은 문제
		- 최악의 경우의 수를 계산하는 가장 쉬운 방법
			- 직접 계산해보는 방법
				- 초반부에 직접 계산해보면 패턴이 보일 것이고 그 패턴으로 최대 경우의 수를 유추할 수 있다. 그리고 DP에 사용하기 적합한지 여부를 판단.
		2. 경우의 수들에 중복적인 연산이 많은 경우
- 풀이법
	- 최대한 많은 문제들을 풀어보고 풀이들을 참고하면서
	- DP식 사고방식을 습득할 필요가 있다.
	- 혼자서 스스로 풀이하기에는 아주 많은 시간이 걸린다.
	- 오래 붙잡고 있기보다는 30분 정도 고민해보고 답이 안나오면 풀이를 참고해서 구현만 해보는 방식을 강하게 추천
	- 30분동안은 어떻게하면 뒤로 돌아가지 않을 수 있을까를 고민
	- 현재 단계까지는 연산을 잘했는데 그 연산을 또 하지않으려면 어떤 정보를 남겨야 하지?
	- 어떤 식으로 정보를 누적해야되지?
	- DP 삼각형 같이 나만의 자료구조를 하나 더 만들고 거기에 어떤 정보를 담아야 이전 단계로 돌아가지 않을지 고민해 봐야한다. 
	  
- 코드
```java
// 미로 탈출 문제 (DFS)

public class MazeEscape {
    private static final int[] dx = {-1, 1, 0, 0};  // 상, 하, 좌, 우
    private static final int[] dy = {0, 0, -1, 1};
	
    public static boolean canEscape(
    int[][] maze, int startX, int startY, int endX, int endY) {
    
        int m = maze.length;
        int n = maze[0].length;
        
        // 방문 여부를 체크할 배열
        boolean[][] visited = new boolean[m][n];
        
        // DFS 탐색
        return dfs(maze, startX, startY, endX, endY, visited);
    }
	
    private static boolean dfs(
    int[][] maze, int x, int y, int endX, int endY, boolean[][] visited) {
    
        // 경계를 벗어나거나 벽에 막혔을 때
        if (x < 0 || x >= maze.length 
        || y < 0 
        || y >= maze[0].length 
        || maze[x][y] == 1 
        || visited[x][y]) {
        
            return false;
        }
		
        // 도착지점에 도달했을 경우
        if (x == endX && y == endY) {
            return true;
        }

        visited[x][y] = true;

        // 4방향으로 이동 시도
        for (int i = 0; i < 4; i++) {
            int newX = x + dx[i];
            int newY = y + dy[i];

            // DFS를 통해 탈출 가능 여부 확인
            if (dfs(maze, newX, newY, endX, endY, visited)) {
                return true;
            }
        }

        return false;  // 탈출 불가능
    }

    public static void main(String[] args) {
        // 0은 길, 1은 벽
        int[][] maze = {
            {0, 1, 0, 0, 0},
            {0, 1, 0, 1, 0},
            {0, 0, 0, 1, 0},
            {1, 1, 0, 1, 0},
            {0, 0, 0, 0, 0}
        };
        
        // 시작점 (0,0)에서 종료점 (4,4)로 탈출 가능한지 확인
        if (canEscape(maze, 0, 0, 4, 4)) {
            System.out.println("탈출 가능!");
        } else {
            System.out.println("탈출 불가능!");
        }
    }
}

//`maze`는 미로를 나타내는 2D 배열입니다. `0`은 길, `1`은 벽을 의미.
// `dfs` 함수는 깊이 우선 탐색을 사용하여 
// 현재 위치에서 출구로 가는 경로가 있는지 찾는다.
// 4방향으로 이동할 수 있도록 `dx`, `dy` 배열을 사용해 상하좌우를 탐색한한다.

```
	
- 학습 자료
	- https://www.youtube.com/watch?v=0bqfTzpWySY
