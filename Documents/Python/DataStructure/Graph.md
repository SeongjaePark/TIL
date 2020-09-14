# 3. 그래프

[코드잇 자료구조 코스](https://www.codeit.kr/courses/data-structures)

<details>
  <summary>1) 그래프란?</summary>
  <details>
    <summary>연결 관계 데이터와 그래프 & 그래프 기본 용어 정리</summary>

# 연결 관계 데이터와 그래프

우리가 자료 구조를 공부하는 이유 중 하나는, 상황에 맞는 방식으로 데이터를 저장하고 사용하기 위함임. 데이터 사이에 어떤 관계가 있는지에 따라 적절한 자료 구조를 골라서 사용해야 함.

전후 관계를 저장하고 싶으면 배열이나 링크드 리스트처럼 선형적 자료 구조를, 계층적 관계를 저장하고 싶으면 트리를 사용하면 됨

## 그래프

그래프는 연결 관계를 표현하기 위해 사용함

연괄 관계 예시: 위치 데이터, 사회 연결망

### 다양한 연결 관계

- 통신: 수많은 컴퓨터들의 연결 관계인 인터넷
- 생물: 유전자와 단백질의 상호 작용 관계

# 그래프 용어 / 성질 정리

## 그래프 기본 용어

- 노드: 그래프에서 하나의 데이터 단위를 나타내는 객체.
- 엣지: 그래프에서 두 노드의 직접적인 연결 관계 데이터. 두 노드 사이에 엣지가 있을 때, "두 노드는 인접해 있다"라고 표현함. 엣지가 갖는 특성에 따라 그래프의 종류가 나뉘기도 함
  - 방향 그래프 (directed graph): 방향 그래프에서는 엣지들이 방향을 갖는다. 인스타그램의 팔로우 관계처럼 한 유저가 다른 유저를 팔로우하는 일방적인 관계를 나타낼 수 있게 해준다.
  - 가중치 그래프 (weighted graph): 가중치 그래프에서는 엣지들의 연결 관계뿐만 아니라 어떤 정보를 나타내는 수치를 가진다. 그 정보는 예를 들자면 친구 관계에서는 친밀도, 위치 정보 그래프면 두 장소 사이의 거리 같은 것이다.
- 차수(degree): 하나의 노드에 연결된 엣지들의 수
  - 무방향 그래프(undirected graph)에서는 하나의 노드에 연결된 엣지들의 수를 나타내고, 방향 그래프에서는 노드를 떠나는 엣지의 수를 출력 차수(outdegree), 노드에 들어오는 엣지의 수를 입력 차수(indegree)로 구별해서 부른다.
- 경로: 한 노드에서 다른 노드까지 가는 길. 두 노드가 서로 인접해있지 않다고 해서 두 노드 사이의 경로가 없는 건 아니다. 두 노드 사이를 이어주는 길을 경로라고 한다
  - 경로의 거리
    - 비가중치 그래프: 한 경로에 있는 엣지의 수
    - 가중치 그래프: 한 경로에 있는 엣지의 가중치의 합
  - 최단 경로: 두 노드 사이의 경로 중 거리가 가장 짧은 경로
  - 사이클: 한 노드에서 시작해서 같은 노드로 돌아오는 경로

## 연결된 그래프

그래프는 여러 개의 노드와 엣지들을 갖지만, 그래프 안에 있는 모든 노드들이 서로 경로를 통해 연결될 필요는 없다.

서로 연결된 노드들의 집합이 서로 나누어져 있을 수도 있고, 조금 더 극단적인 예시를 보면 아예 엣지가 없고 노드만 있는 그래프도 있을 수 있는 것이다.

  </details>
  <details>
    <summary>그래프 노드 구현</summary>

# 그래프 노드 구현

```python
class StationNode:
  """지하철 역 노드를 나타내는 클래스"""
  def __init__(self, name, num_exits):
    self.name = name
    self.num_exits = num_exits

# 지하철 역 노드 인스턴스 생성
station_0 = StationNode("교대역", "14")
station_1 = StationNode("사당역", "14")
station_2 = StationNode("종로3가역", "16")
station_3 = StationNode("서울역", "16")

# 노드들을 파이썬 리스트에 저장 (해시 테이블로 구현되어 있음)
# 노드의 각 고유한 인덱스를 통해 빠르게 접근할 수 있음
stations = [station_0, station_1, station_2, station_3]

print(stations[3].name) # 서울역

# 지하철 역 노드들을 파이썬 딕셔너리에 저장
# 좀 더 직관적으로 노드들을 가져올 수 있음
stations = {
  "교대역": station_0,
  "사당역": station_1,
  "종로3가역": station_2,
  "서울역": station_3
}

node_1 = stations["교대역"]
node_2 = stations["서울역"]

# 만약 SNS에서 이름을 key로 사용하는 경우 key가 겹치는 경우가 발생
# 그럴 땐 사용자의 이메일 주소와 같이 겹치지 않는 것을 key로 사용하면 됨
```

# 그래프 노드 만들어보기

stations.txt 파일에는 각 줄에 각 호선의 역 이름이 "소요산 - 동두천 - 보산 ... " 이런 식으로 저장되어 있다.

```python
class StationNode:
    """간단한 지하철 역 노드 클래스"""
    def __init__(self, station_name):
        self.station_name = station_name


def create_station_nodes(input_file):
    """input_file에서 데이터를 읽어 와서 지하철 그래프 노드들을 리턴하는 함수"""
    stations = {}  # 지하철 역 노드들을 담을 딕셔너리

    # 파라미터로 받은 input_file 파일을 연다
    with open(input_file) as stations_raw_file:
        for line in stations_raw_file:  # 파일을 한 줄씩 받아온다
            subway_line = line.strip().split("-")  # 앞 뒤 띄어쓰기를 없애고 "-"를 기준점으로 데이터를 나눈다

            for name in subway_line:
                station_name = name.strip()  # 앞 뒤 띄어쓰기 없애기

                # 지하철 역 이름이 이미 저장된 key인지 확인
                if station_name not in stations:
                    # 새로운 노드 인스턴스를 생성하고
                    current_station = StationNode(station_name)
                    # dictionary에 역 이름은 key로, 역 노드 인스턴스를 value로 저장한다
                    stations[station_name] = current_station

    return stations

stations = create_station_nodes("./stations.txt")  # stations.txt 파일로 그래프 노드들을 만든다

# stations에 저장한 역들 이름 출력 (체점을 위해 역 이름 순서대로 출력)
for station in sorted(stations.keys()):
    print(stations[station].station_name)
```

  </details>
  <details>
    <summary>엣지 구현</summary>

# 엣지 구현 1: 인접 행렬

## 인접 행렬

- 각 노드를 배열 또는 파이썬 리스트에 저장해 고유 정수 인덱스를 준다
- 노드 수 X 노드 수 크기의 행렬을 만든다
- 노드들의 엣지 유무 및 가중치에 따라 행렬의 요소를 채운다.

# 인접 행렬 구현

## 구현할 그래프

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48f3b4f7-1b81-4ab1-a34f-8b522d396932/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48f3b4f7-1b81-4ab1-a34f-8b522d396932/Untitled.png)

위에 있는 무방향 그래프를 구현하자. 각 노드 위나 옆에 있는 정수가 노드의 고유 숫자이다. 이 고유 숫자를 행렬의 인덱스로 사용한다.

## 내가 짠 코드

```python
# 모든 요소를 0으로 초기화시킨 크기 6 x 6 인접 행렬
adjacency_matrix = [[0 for i in range(6)] for i in range(6)]

adjacency_matrix[0] = [0, 1, 1, 0, 0, 0]
adjacency_matrix[1] = [1, 0, 0, 1, 0, 1]
adjacency_matrix[2] = [1, 0, 0, 0, 0, 1]
adjacency_matrix[3] = [0, 1, 0, 0, 1, 1]
adjacency_matrix[4] = [0, 0, 0, 1, 0, 1]
adjacency_matrix[5] = [0, 1, 1, 1, 1, 0]

print(adjacency_matrix)
```

## 다른 회원 코드

```python
# 모든 요소를 0으로 초기화시킨 크기 6 x 6 인접 행렬
adjacency_matrix = [[0 for i in range(6)] for i in range(6)]

adjacency_matrix[0][1]=1
adjacency_matrix[0][2]=1
adjacency_matrix[1][3]=1
adjacency_matrix[1][5]=1
adjacency_matrix[2][5]=1
adjacency_matrix[3][4]=1
adjacency_matrix[3][5]=1
adjacency_matrix[4][5]=1

# 나머지 절반 자동으로 채우기 (i와 j 순서에 유의)
for i in range(6):
    for j in range(6):
        adjacency_matrix[j][i]=adjacency_matrix[i][j]

print(adjacency_matrix)
```

# 엣지 구현 2: 인접 리스트

## 인접 리스트

- 각 노드의 엣지를 리스트에 저장하는 방법
- 각 노드마다 스스로 연결된 노드들에 대한 레퍼런스를 리스트로 저장
- 가중치 그래프의 경우 연결된 노드에 대한 레퍼런스와 가중치를 튜플에 저장 ex) [(노드1, 3), (노드2, 5)]

# 인접 리스트 연습

### StationNode.py

```python
class StationNode:
    """간단한 지하철 역 노드 클래스"""
    def __init__(self, station_name):
        self.station_name = station_name
        self.adjacent_stations = []  # 인접 리스트

    def add_connection(self, other_station):
        """지하철 역 노드 사이 엣지 저장하기"""
        self.adjacent_stations.append(other_station)
        other_station.adjacent_stations.append(self)

    def __str__(self):
        """지하철 노드 문자열 메소드. 지하철 역 이름과 연결된 역들을 모두 출력해준다"""
        res_str = f"{self.station_name}: "  # 리턴할 문자열

        # 리턴할 문자열에 인접한 역 이름들 저장
        for station in self.adjacent_stations:
            res_str += f"{station.station_name} "

        return res_str
```

### 내가 쓴 main.py

```python
from StationNode import *

# 코드를 추가하세요
def create_subway_graph(input_file):
    """input_file에서 데이터를 읽어 와서 지하철 그래프를 리턴하는 함수"""
    stations = {}  # 지하철 역 노드들을 담을 딕셔너리

    # 파라미터로 받은 input_file 파일을 연다
    with open(input_file) as stations_raw_file:
        for line in stations_raw_file:  # 파일을 한 줄씩 받아온다
            subway_line = line.strip().split("-")  # 앞 뒤 띄어쓰기를 없애고 "-"를 기준점으로 데이터를 나눈다

            for name in subway_line:
                station_name = name.strip()  # 앞 뒤 띄어쓰기 없애기

                # 지하철 역 이름이 이미 저장한 key 인지 확인
                if station_name not in stations:
                    current_station = StationNode(station_name)  # 새로운 인스턴스를 생성하고
                    stations[station_name] = current_station  # dictionary에 역 이름은 key로, 역 노드 인스턴스를 value로 저장한다

						# 첫번째 역부터 마지막에서 두번째 역까지 돈다
            for i in range(len(subway_line) - 1):
								# 현재 역과 다음 역의 이름을 받아온다
                current_station_name = subway_line[i].strip()
                next_station_name = subway_line[i+1].strip()

								# 현재 역과 다음 역의 노드 인스턴스를 각각 받아온다
                current_station = stations[current_station_name]
                next_station = stations[next_station_name]

                # 서로 인접한 두 역 사이의 엣지를 생성한다
								current_station.add_connection(next_station)


    return stations

stations = create_subway_graph("./stations.txt")  # stations.txt 파일로 그래프를 만든다

# stations에 저장한 역 인접 역들 출력 (체점을 위해 역 이름 순서대로 출력)
for station in sorted(stations.keys()):
        print(stations[station])
```

### 코드잇 해설 [main.py](http://main.py) (더 나은 코드)

```python
from StationNode import *

# 코드를 추가하세요
def create_subway_graph(input_file):
    """input_file에서 데이터를 읽어 와서 지하철 그래프를 리턴하는 함수"""
    stations = {}  # 지하철 역 노드들을 담을 딕셔너리

    # 파라미터로 받은 input_file 파일을 연다
    with open(input_file) as stations_raw_file:
        for line in stations_raw_file:  # 파일을 한 줄씩 받아온다
            subway_line = line.strip().split("-")  # 앞 뒤 띄어쓰기를 없애고 "-"를 기준점으로 데이터를 나눈다

            # 엣지를 저장하기 위한 도우미 변수. 현재 보고 있는 역 전 역을 저장한다
            previous_station = None

            for name in subway_line:
                station_name = name.strip()  # 앞 뒤 띄어쓰기 없애기

                # 지하철    역 이름이 이미 저장한 key 인지 확인
                if station_name not in stations:
                    current_station = StationNode(station_name)  # 새로운 인스턴스를 생성하고
                    stations[station_name] = current_station  # dictionary에 역 이름은 key로, 역 노드 인스턴스를 value로 저장한다
                # 이미 저장한 역이면 stations에서 역 인스턴스를 갖고 온다
                else:
                    current_station = stations[station_name]

                if previous_station is not None:
                    # 현재 역과 전 역의 엣지를 연결한다
                    current_station.add_connection(previous_station)

                # 현재 역을 전 역으로 저장
                previous_station = current_station

    return stations

stations = create_subway_graph("./stations.txt")  # stations.txt 파일로 그래프를 만든다

# stations에 저장한 역 인접 역들 출력 (체점을 위해 역 이름 순서대로 출력)
for station in sorted(stations.keys()):
        print(stations[station])
```

해설에서 제공한 코드에서는 도우미 변수 previous_station을 이용하여, 내 코드처럼 굳이 반복문을 한 번 더 돌지 않아도 되어서 더 효율적인 것으로 보인다.

  </details>
  <details>
    <summary>인접 행렬 vs 인접 리스트</summary>

# 인접 행렬 vs 인접 리스트

## 복잡도 표현 기호

보통 다른 자료 구조들을 공부할 때는 들어있는 데이터 수를 n이라고 했음.

그래프를 분석할 때는 다른 알파벳들을 씀.

### _V_

*V*는 그래프 안에 있는 모든 노드들의 집합.

그래프에 있는 하나의 데이터 객체를 노드라고도 부르지만, Vertex라는 표현을 사용하기도 함.

### _E_

*E*는 그래프 안에 있는 모든 엣지(Edge)들의 집합.

원래 *V*와 *E*는 노드와 엣지의 수를 나타내는 건 아닌데, 점근 표기법에서 사용할 때 *V*는 모든 노드의 수, 그리고 *E*를 모든 엣지의 수로 사용하기도 한다.

### *V*와 *E*의 관계

노드 수가 *V*일 때 그래프 안에는 최대 몇 개의 엣지가 있을 수 있을까?

- 무방향 그래프: V^(2)/2
- 방향 그래프: V^(2)

두 경우 모두 V^(2)에 비례하는 만큼의 엣지를 가질 수 있음. 그렇기 때문에 *E*는 최악의 경우 V^(2)에 비례함.

그래프를 배울 때는 O(n), O(lg(n)) 이런 점근 표기법 대신 O(V), O(E), O(lg(V)) 이렇게 표시를 한다.

## 노드를 저장하는 공간

일단 인접 행렬을 사용하던 인접 리스트를 사용하던 노드들을 저장해야 되는데, 총 *V*개의 노드를 저장하기 때문에 노드를 저장하는 데에는 **O(V)**의 공간을 사용한다고 할 수 있음.

## 인접 행렬이 차지하는 공간

인접 행렬을 정의할 때에는 "총 노드의 수 x 총 노드의 수"만큼의 행렬을 만들었음

그래프 안에 있는 노드의 수가 *V*라고 할 때 인접 행렬은 _V_ x _V_ 크기의 행렬을 저장하고 각 요소들이 0 또는 1을 저장했음. 그럼 총 V^(2)개의 정수를 저장한 것임. 따라서 인접 행렬은 총 V^(2)에 비례하는 공간, **O(V^(2))**의 공간을 차지함

## 인접 리스트가 차지하는 공간

인접 리스트는 각 노드가 자신과 인접한 노드들을 가리키는 레퍼런스를 저장하고 있다

일단 모든 노드는 하나의 인접 리스트를 갖는다. 따라서 총 *V*개의 배열 또는 파이썬 리스트를 저장해야 함. *V*에 비례하기 때문에 일단 최소 O(V) 만큼의 공간을 차지한다.

그럼 엣지를 저장하는데는 얼만큼의 공간을 사용할까? 모든 노드에 저장된 엣지 데이터를 다 합치면 무방향 그래프일 때 _2E_, 방향 그래프일 때는 *E*이다. (무방향 그래프는 똑같은 엣지를 2개씩 저장하기 때문). 총 저장하는 레퍼런스 수는 *E*에 비례한다고 할 수 있음. **O(E)**

그럼에도 불구하고 *E*는 최악의 경우 (모든 노드가 서로 다른 모든 노드에 연결된 경우) V^(2)에 비례.

그렇기 때문에 O(V+E)라고 볼 수도 있겠지만, E=O(V^(2))라는 최악의 경우를 생각하면 읹버 리스트도 O(V^(2))의 공간을 차지한다고 할 수 있음

하지만 좀 더 공간 복잡도를 현실적으로 표기하기 위해 주로 O(V+E)라고 한다.

## 두 노드가 연결됐는지 확인하는 데 걸리는 시간

**인접 행렬**을 이용하면 두 노드가 인접하는지 아닌지를 O(1)로 알아낼 수 있음.

ex) `adjacency_matrix[3][5]`

**인접 리스트**는 어떨까?

```python
gangnam_station = stations["강남"]
seocho_station = stations["서초"]

print(seocho_stations in gangnam_station.adjacent_stations)
```

이런 식으로 한 노드의 리스트 안에 특정 역이 저장됐는지를 탐색해야 함. 선형 탐색을 해야하기 때문에 리스트 안에 있는 데이터를 다 돌아야 한다. 몇 개의 데이터가 있는지에 따라 다르겠지만, 최악의 경우 *V*개의 요소를 확인해야 함

## 한 노드에 연결된 모든 노드들을 알아내는 데 걸리는 시간

주로 한 노드에 연결된 모든 노드를 가지고 오는 작업을 많이 한다면 어떤 방법을 사용하는 게 좋을까?

인접 행렬에서는 한 노드를 나타내는 배열, 또는 파이썬 리스트 전체를 다 돌아야지만 그 노드가 연결된 다른 노드들을 갖고 올 수 있다. 그러니까 리스트 안에 있는 데이터를 하나씩 돌면서 0인지 1인지 확인해야 된다. 모든 리스트 안에는 총 *V*개의 데이터 요소가 들어 있으니까 매번 *V*번 돌아야 한다.

인접 리스트를 쓸 때는 각 노드가 자신과 인접한 노드들에 대한 레퍼런스만 갖고 있다. 물론 최악의 경우 한 노드가 다른 모든 노드들과 연결되어 있으면, 인접 행렬과 마찬가지로 총 *V*번 돌아서 인접한 노드들을 가지고 와야되기는 하지만, 그런 경우는 그렇게 많지 않다. 대부분의 경우 인접 행렬을 사용하는 것보다 더 빠르게 실행된다.

결국 위와 같은 용도로는 인접 리스트를 사용하는 게 인접 행렬을 사용하는 것보다 좀 더 효율적이다.

  </details>
</details>
<details>
  <summary>2) 그래프 탐색</summary>
</details>
<details>
  <summary>3) 최단 경로 알고리즘</summary>
</details>
