## Example CMake project with two subdirectories which depend on each other 
### Problem
You have a CMake project with two subprojects A and B added by `add_subdirectory()`. Assume A and B are external (independent) CMake projects so you don't want to modify them. B depends on A and B searchs for A using `find_package()` in `CONFIG` mode which fails since `AConfig.cmake` (and `AConfigVersion.cmake`) is created after `find_package()` is executed.

### Workaround
Create a dummy file `AConfig.cmake` (and `AConfigVersion.cmake`)
