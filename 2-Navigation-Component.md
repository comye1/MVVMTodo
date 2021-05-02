# #2 Navigation Component

## 꿀팁
- 패키지 펼치기
- ![image](https://user-images.githubusercontent.com/50735594/116652366-00f80000-a9c0-11eb-96e1-4a4448406c13.png)

## res / navigation / nav_graph
- navigation graph 정의

## ui 패키지
- tasks 패키지에 TasksFragment
```Kotlin
class TasksFragment : Fragment(R.layout.fragment_tasks) {}
```
- MainActivity 포함

## fragment_tasks.xml
- TasksFragment와 결합하기 : parent layout의 tools:context속성에 지정

## activity_main.xml
- FragmentContainerView : fragment 네비게이션을 담을 뷰
  - name 속성에 "androidx.navigation.fragment.NavHostFragment" 지정
  - defaultNavHost 속성 true 지정
  - navGraph 속성에 위에서 정의한 nav_graph 지정
