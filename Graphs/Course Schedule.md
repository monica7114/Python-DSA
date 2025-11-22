#Course Schedule
## Topological Sort (Kahn's Algorithm)
``` python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        adj = defaultdict(list)
        in_degree = [0] * numCourses
        for course,prereq in prerequisites:
            adj[prereq].append(course)
            in_degree[course]+=1
        q=deque()
        for i in range(numCourses):
            if in_degree[i]==0:
                q.append(i)
        course_taken=0
        while q:
            course=q.popleft()
            course_taken+=1
            for nei in adj[course]:
                in_degree[nei]-=1
                if in_degree[nei]==0:
                    q.append(nei)
        return course_taken==numCourses
```
