# #3 Room Dependency Injection

## data / TaskDao.kt 
- interface
- methods for Database operations
	- suspend fun insert
	- suspend fun update
	- suspend fun delete
	- fun getTasks -> return Flow<List\<Task>>  
	> Flow? 
	a type that can emit multiple values **sequentially**, as opposed to **_suspend functions_** that return only a single value. For example, you can use a flow to receive live updates from a database. https://developer.android.com/kotlin/flow
## data / TaskDatabase.kt
- abstract class TaskDatabse : extends RoomDatabase
	- abstract fun taskDao
All your files and folders are presented as a tree in the file explorer. You can switch from one to another by clicking a file in the tree.

## Dagger-Hilt
- Dependency Injection Library
	## ui / MainActivity.kt
	- @AndroidEntryPoint
	## ui / tasks / TasksFragment.kt
	- @AndroidEntryPoint
	## ui / tasks / TasksViewModel.kt
	- @ViewModelInject (constructor parameter taskDao)
	## di / AppModule.kt
	- object
	- @Module @InstallIn
	 - @Proivides @Singleton fun provideDatabase
	 -  @Provides fun provideTaskDao 
	 - @ApplicationScope @Provides @Singleton fun provideApplicationScope()
	 - @Retention(AnnotationRetention.RUNTIME) @Qualifier annotation class ApplicationScope
	 ## TaskDatabase.kt
	 - class Callback 
	```
    class Callback @Inject constructor(
        private val database: Provider<TaskDatabase>,
        @ApplicationScope private val applicationScope: CoroutineScope
    ): RoomDatabase.Callback() {
        override fun onCreate(db: SupportSQLiteDatabase) {
            super.onCreate(db)

            val dao = database.get().taskDao()

            applicationScope.launch {
                dao.insert(Task("Wash the dishes"))
                dao.insert(Task("Do the laundry"))
                dao.insert(Task("Buy groceries"))
                dao.insert(Task("Prepare food", completed = true))
                dao.insert(Task("Have lunch", completed = true))
                dao.insert(Task("Study for the exam", important = true))
            }
        }
    }
    ```
