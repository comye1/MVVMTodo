Watch the course here: https://www.youtube.com/playlist?list=PLrnPJCHvNZuCfAe7QK2BoMPkv2TGM_b0E
https://github.com/codinginflow/MVVMTodo

# #1 Layouts & Room Entity

## 꿀팁
-- ctrl + alt + L : 코드 정리 (formatting)
-- CoordinateLayout : FAB를 위해
-- Parcelable Class : 프래그먼트간 전달을 위해

	## fragment_tasks.xml
	- CoordinatorLayout : parent
	- RecyclerView
	- FloatingActionButton

	## item_tasks.xml
	- RelativeLayout : parent
	-- layout_alignParentStart/End/Top/Bottom
	-- layout_alignStart/End/Top/Bottom
	-- layout_toStartOf/toEndOf/toTopOf/toBottomOf
	- CheckBox
	- TextView
	-- maxLines
	-- elilipsized="end" **If set, causes words that are longer than the view is wide to be ellipsized instead of broken in the middle.**
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