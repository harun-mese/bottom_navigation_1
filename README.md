# Bottom Navigation Screenshot

<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_home.png?raw=true" width="170"/>
<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_groups.png?raw=true" width="170"/>
<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_arc.png?raw=true" width="170"/>
<img align="left" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_stories.png?raw=true" width="170"/>
<img align="center" src="https://github.com/harun-mese/bottom_navigation_1/blob/master/app/src/main/res/drawable/bn_profile.png?raw=true" width="170"/>

<hr>

***Steps***

### viewBinding
Step 1

```kotlin
android {
    buildFeatures{
        viewBinding = true
    }
}
```

### implementation
Step 1
```kotlin
dependencies {
    implementation("androidx.navigation:navigation-fragment-ktx:2.7.7")
    implementation("androidx.navigation:navigation-ui-ktx:2.7.7")
}
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
