# CS300

RUNTIME ANALYSIS: 
Vector, hash table, and binary search tree all come with its own pros and cons. The vector is simple and easy to use, especially for beginners. It works fine for storing and displaying data, and it’s easy to sort it alphanumerically. However, searching through a vector to find a specific course or to validate prerequisites takes longer since it often has to check every item one by one. This makes it slower as the number of courses increases.
The hash table is the fastest option when it comes to looking up a specific course. Since it uses keys and hashing, it can find and store data really quickly. This is useful for checking prerequisites and searching for a course by its number. The downside is that it doesn’t keep the courses in any particular order, so if you need to print them alphabetically, you have to copy everything into a separate structure like a vector and then sort it. There’s also a small risk of collisions, which can slow things down, but it’s still usually faster than the other two.
The binary search tree is a good middle ground. It keeps data in sorted order by default, which makes it great for printing all courses in order without extra steps. It also allows for fairly quick lookups, especially if the tree stays balanced. The main issue with trees is that if they get unbalanced (like if all the course numbers are in order when added), they can become very slow, basically turning into a linked list. That can make searching and inserting much slower in those cases.
Overall, if fast lookups are the top priority, like quickly finding a course or checking its prerequisites, the hash table is the best choice. If keeping the courses sorted automatically is more important, the binary search tree is better. The vector is the easiest to work with but becomes inefficient for larger datasets or when frequent searching is needed.

After comparing the vector, hash table, and binary search tree, I recommend using the hash table for this program. Based on the Big O analysis, the hash table had the most efficient average runtime, especially for searching and validating course prerequisites. Its average case performance is O(nm), which is faster than the vector’s O(n²m) and slightly better than the binary search tree’s O(nm log n). Although the hash table doesn’t store courses in order, this can be easily handled by copying the data to a vector when needed for sorting. The hash table is also great for quickly finding individual courses by course number, which is one of the main features we want. While the binary search tree is helpful for keeping the data sorted, and the vector is simple to use, the hash table offers the best balance of speed and flexibility for the program’s core requirements.

WORKING CODE THAT SORT AND PRINT OUT A LIST OF THE COURSES IN THE COMPUTER SCIENCE PROGRAM IN ALPHANUMERIC ORDER: 
// Print all courses in alphanumeric order
void printAllCourses(HashTable& courseTable) {
    vector<Course> courses = courseTable.getAllCourses();
    sort(courses.begin(), courses.end(), [](const Course& a, const Course& b) {
        return a.courseNumber < b.courseNumber;
    });

    cout << "Here is a sample schedule:" << endl;
    for (Course course : courses) {
        cout << course.courseNumber << ", " << course.courseTitle << endl;
    }
}
REFLECTION: 
One major problem I encountered during these projects was figuring out which data structure would best handle storing and searching for course information. At first, using a simple vector seemed fine, but as the project requirements grew, needing faster search times and validation of prerequisites, I realized a vector alone was not efficient enough. Searching through an unsorted list for every course or prerequisite would quickly become slow and messy.

Switching to a hash table was the key solution. I had to learn how to properly hash course numbers and handle collisions using separate chaining. Once I made the switch, searching for a course by its number became almost instant no matter how many courses were loaded. This experience showed me firsthand why understanding different data structures is so important. The right choice can completely change the performance and organization of a program.

Solving this problem expanded how I think about designing software. Now, I do not just jump into writing code. I step back and ask myself which data structure makes the most sense based on what the program needs to do. It also helped me write more maintainable and readable code because organizing data correctly from the start made everything else, like sorting, searching, and printing, much cleaner and easier to manage.
