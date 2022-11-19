 >**NEED TO USE HEAP SPACE NOT PHYSICAL SPACE IN MEMORY**

Using frigg as a allocator manager we can skip all the difficult management of header and data sections and just leave it to frigg to sort them out. All I need to do is tell frigg what pages and memory locations it can give out (What has been mapped).