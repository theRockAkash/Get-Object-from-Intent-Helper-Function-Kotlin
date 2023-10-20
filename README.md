# Get-Object-from-Intent-Helper-Function-Kotlin


 Add this as a global function like Extention function in any kotlin file outside of class
```
inline fun <reified T : Serializable> Intent.getSerializableObjectExtra(key: String, clazz: Class<T>): T? {
    return if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
        getSerializableExtra(key, clazz)
    } else {
        val temp = getSerializableExtra(key)
        if (temp is T)
            temp
        else null
    }
}
```
