# Bottom Navigation Screenshots

<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_home.png?raw=true" width="170"/>
<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_groups.png?raw=true" width="170"/>
<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_arc.png?raw=true" width="170"/>
<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_stories.png?raw=true" width="170"/>
<img align="center" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_profile.png?raw=true" width="170"/>

<hr>

viewBinding
```kotlin
android {
    buildFeatures{
        viewBinding = true
    }
}
```


Implementation dependencies 

```kotlin
dependencies {
    implementation("androidx.navigation:navigation-fragment-ktx:2.7.7")
    implementation("androidx.navigation:navigation-ui-ktx:2.7.7")
}
```

### app_menu.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item
        android:id="@+id/nav1Fragment"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:icon="@drawable/houseboat"
        android:title="@string/nav1" />
    <item
        android:id="@+id/nav2Fragment"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:icon="@drawable/groups"
        android:title="@string/nav2" />
    <item
        android:id="@+id/nav3Fragment"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:icon="@drawable/agriculture"
        android:title="@string/nav3" />
    <item
        android:id="@+id/nav4Fragment"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:icon="@drawable/stories"
        android:title="@string/nav4" />
    <item
        android:id="@+id/nav5Fragment"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:icon="@drawable/flutter_dash"
        android:title="@string/nav5" />
</menu>
```
### nav_graph.xml

```xml
<<?xml version="1.0" encoding="utf-8"?>
<navigation xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/nav_graph"
    app:startDestination="@id/nav1Fragment">

    <fragment
        android:id="@+id/nav1Fragment"
        android:name="www.harunmese.dev.bottomnavigation1.Nav1Fragment"
        android:label="fragment_nav1"
        tools:layout="@layout/fragment_nav1" />
    <fragment
        android:id="@+id/nav2Fragment"
        android:name="www.harunmese.dev.bottomnavigation1.Nav2Fragment"
        android:label="fragment_nav2"
        tools:layout="@layout/fragment_nav2" />
    <fragment
        android:id="@+id/nav3Fragment"
        android:name="www.harunmese.dev.bottomnavigation1.Nav3Fragment"
        android:label="fragment_nav3"
        tools:layout="@layout/fragment_nav3" />
    <fragment
        android:id="@+id/nav4Fragment"
        android:name="www.harunmese.dev.bottomnavigation1.Nav4Fragment"
        android:label="fragment_nav4"
        tools:layout="@layout/fragment_nav4" />
    <fragment
        android:id="@+id/nav5Fragment"
        android:name="www.harunmese.dev.bottomnavigation1.Nav5Fragment"
        android:label="fragment_nav5"
        tools:layout="@layout/fragment_nav5" />
</navigation>/androidx.constraintlayout.widget.ConstraintLayout>

```
### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/bottomNavigationView"
        android:layout_width="0dp"
        android:layout_height="60dp"
        app:backgroundTint="#FFFFFF"
        app:itemIconTint="@drawable/app_nav_selector"
        app:labelVisibilityMode="unlabeled"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:menu="@menu/app_menu" />

    <androidx.fragment.app.FragmentContainerView
        android:id="@+id/fragmentContainerView"
        android:name="androidx.navigation.fragment.NavHostFragment"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:background="@color/white"
        app:defaultNavHost="true"
        app:layout_constraintBottom_toTopOf="@+id/bottomNavigationView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:navGraph="@navigation/nav_graph" />
</androidx.constraintlayout.widget.ConstraintLayout>

```
### MainActivity

```kotlin
class MainActivity : AppCompatActivity() {

    private lateinit var binding : ActivityMainBinding
    private lateinit var navController: NavController

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        val view = binding.root
        setContentView(view)


        val navHostFragment = supportFragmentManager.findFragmentById(R.id.fragmentContainerView) as NavHostFragment
        navController = navHostFragment.navController
        setupWithNavController(binding.bottomNavigationView,navController)
    }
}
```
