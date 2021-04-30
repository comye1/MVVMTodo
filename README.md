Watch the course here: https://www.youtube.com/playlist?list=PLrnPJCHvNZuCfAe7QK2BoMPkv2TGM_b0E
https://github.com/codinginflow/MVVMTodo

# #1 Layouts & Room Entity

## 꿀팁
- ctrl + alt + L : 코드 정리 (formatting)
- CoordinateLayout : FAB를 위해
- Parcelable Class : 프래그먼트간 전달을 위해

## fragment_tasks.xml
- CoordinatorLayout : parent
- RecyclerView
- FloatingActionButton

## item_tasks.xml
- RelativeLayout : parent
  - layout_alignParentStart/End/Top/Bottom
  - layout_alignStart/End/Top/Bottom
  - layout_toStartOf/toEndOf/toTopOf/toBottomOf
- CheckBox
- TextView
  - maxLines
  - elilipsized="end" **If set, causes words that are longer than the view is wide to be ellipsized instead of broken in the middle.**
- ImageView

## fragment_add_edit_task.xml
- CoordinateLayout : parent
- LinearLayout
- EditText
- CheckBox
- FloatingActionButton
- TextView

## data / Task.kt
- data class for Room (= Entity)
- name, important, completed, created, id
- createdDataFormatted <- get from created

---

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
