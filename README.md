**Name:** Abdelouahed Akharaze

**GitHub:** https://github.com/abdelouahedakharaze

**Name:** Abdelouahed Akharaze

**GitHub:** https://github.com/abdelouahedakharaze



---

**_0. Bubble sort_**

---

<p><iframe allowfullscreen="" frameborder="0" height="315" src="https://www.youtube.com/embed/lyZQPjUT5B4" width="560"></iframe><br/>
<br/></p>

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/awhP8BhtkGi-lwmMc2-KAw" target="_blank" title="Bubble sort">Bubble sort</a> algorithm</p>

<p>Write in the file <code>0-O</code>, the big O notations of the time complexity of the Bubble sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 0-main.c 
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    bubble_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 0-bubble_sort.c 0-main.c print_array.c -o bubble
alex@/tmp/sort$ ./bubble
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

19, 48, 71, 99, 13, 52, 96, 73, 86, 7
19, 48, 71, 13, 99, 52, 96, 73, 86, 7
19, 48, 71, 13, 52, 99, 96, 73, 86, 7
19, 48, 71, 13, 52, 96, 99, 73, 86, 7
19, 48, 71, 13, 52, 96, 73, 99, 86, 7
19, 48, 71, 13, 52, 96, 73, 86, 99, 7
19, 48, 71, 13, 52, 96, 73, 86, 7, 99
19, 48, 13, 71, 52, 96, 73, 86, 7, 99
19, 48, 13, 52, 71, 96, 73, 86, 7, 99
19, 48, 13, 52, 71, 73, 96, 86, 7, 99
19, 48, 13, 52, 71, 73, 86, 96, 7, 99
19, 48, 13, 52, 71, 73, 86, 7, 96, 99
19, 13, 48, 52, 71, 73, 86, 7, 96, 99
19, 13, 48, 52, 71, 73, 7, 86, 96, 99
13, 19, 48, 52, 71, 73, 7, 86, 96, 99
13, 19, 48, 52, 71, 7, 73, 86, 96, 99
13, 19, 48, 52, 7, 71, 73, 86, 96, 99
13, 19, 48, 7, 52, 71, 73, 86, 96, 99
13, 19, 7, 48, 52, 71, 73, 86, 96, 99
13, 7, 19, 48, 52, 71, 73, 86, 96, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$ 
</code></pre>

---


---

**_1. Insertion sort_**

---

<p><iframe allowfullscreen="" frameborder="0" height="315" src="https://www.youtube.com/embed/ROalU379l3U" width="560"></iframe><br/>
<br/></p>

<p>Write a function that sorts a doubly linked list of integers in ascending order using the <a href="/rltoken/GocxRKbPdsmERXeOHMCO2w" target="_blank" title="Insertion sort">Insertion sort</a> algorithm</p>

<p>Write in the file <code>1-O</code>, the big O notations of the time complexity of the Insertion sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 1-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * create_listint - Creates a doubly linked list from an array of integers
 *
 * @array: Array to convert to a doubly linked list
 * @size: Size of the array
 *
 * Return: Pointer to the first element of the created list. NULL on failure
 */
listint_t *create_listint(const int *array, size_t size)
{
    listint_t *list;
    listint_t *node;
    int *tmp;

    list = NULL;
    while (size--)
    {
        node = malloc(sizeof(*node));
        if (!node)
            return (NULL);
        tmp = (int *)&amp;node-&gt;n;
        *tmp = array[size];
        node-&gt;next = list;
        node-&gt;prev = NULL;
        list = node;
        if (list-&gt;next)
            list-&gt;next-&gt;prev = list;
    }
    return (list);
}

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    listint_t *list;
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    list = create_listint(array, n);
    if (!list)
        return (1);
    print_list(list);
    printf("\n");
    insertion_sort_list(&amp;list);
    printf("\n");
    print_list(list);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 1-main.c 1-insertion_sort_list.c print_list.c -o insertion
alex@/tmp/sort$ ./insertion
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

19, 48, 71, 99, 13, 52, 96, 73, 86, 7
19, 48, 71, 13, 99, 52, 96, 73, 86, 7
19, 48, 13, 71, 99, 52, 96, 73, 86, 7
19, 13, 48, 71, 99, 52, 96, 73, 86, 7
13, 19, 48, 71, 99, 52, 96, 73, 86, 7
13, 19, 48, 71, 52, 99, 96, 73, 86, 7
13, 19, 48, 52, 71, 99, 96, 73, 86, 7
13, 19, 48, 52, 71, 96, 99, 73, 86, 7
13, 19, 48, 52, 71, 96, 73, 99, 86, 7
13, 19, 48, 52, 71, 73, 96, 99, 86, 7
13, 19, 48, 52, 71, 73, 96, 86, 99, 7
13, 19, 48, 52, 71, 73, 86, 96, 99, 7
13, 19, 48, 52, 71, 73, 86, 96, 7, 99
13, 19, 48, 52, 71, 73, 86, 7, 96, 99
13, 19, 48, 52, 71, 73, 7, 86, 96, 99
13, 19, 48, 52, 71, 7, 73, 86, 96, 99
13, 19, 48, 52, 7, 71, 73, 86, 96, 99
13, 19, 48, 7, 52, 71, 73, 86, 96, 99
13, 19, 7, 48, 52, 71, 73, 86, 96, 99
13, 7, 19, 48, 52, 71, 73, 86, 96, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_2. Selection sort_**

---

<p><iframe allowfullscreen="" frameborder="0" height="315" src="https://www.youtube.com/embed/Ns4TPTC8whw" width="560"></iframe><br/>
<br/></p>

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/SEbg0fBEraioQcl-igvUSw" target="_blank" title="Selection sort">Selection sort</a> algorithm</p>

<p>Write in the file <code>2-O</code>, the big O notations of the time complexity of the Selection sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 2-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    selection_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 
2-main.c 2-selection_sort.c print_array.c -o select
alex@/tmp/sort$ ./select
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

7, 48, 99, 71, 13, 52, 96, 73, 86, 19
7, 13, 99, 71, 48, 52, 96, 73, 86, 19
7, 13, 19, 71, 48, 52, 96, 73, 86, 99
7, 13, 19, 48, 71, 52, 96, 73, 86, 99
7, 13, 19, 48, 52, 71, 96, 73, 86, 99
7, 13, 19, 48, 52, 71, 73, 96, 86, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_3. Quick sort_**

---

<p><iframe allowfullscreen="" frameborder="0" height="315" src="https://www.youtube.com/embed/ywWBy6J5gz8" width="560"></iframe><br/>
<br/></p>

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/_pBTrH0Xyo4BRmQn4CtnMg" target="_blank" title="Quick sort">Quick sort</a> algorithm</p>

<p>Write in the file <code>3-O</code>, the big O notations of the time complexity of the Quick sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 3-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    quick_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 3-main.c 3-quick_sort.c print_array.c -o quick
alex@/tmp/sort$ ./quick
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

7, 48, 99, 71, 13, 52, 96, 73, 86, 19
7, 13, 99, 71, 48, 52, 96, 73, 86, 19
7, 13, 19, 71, 48, 52, 96, 73, 86, 99
7, 13, 19, 71, 48, 52, 73, 96, 86, 99
7, 13, 19, 71, 48, 52, 73, 86, 96, 99
7, 13, 19, 48, 71, 52, 73, 86, 96, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_4. Shell sort - Knuth Sequence_**

---

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/FdpP4Qin3iDAaz1kuPD2Kg" target="_blank" title="Shell sort">Shell sort</a> algorithm, using the <code>Knuth sequence</code></p>

<p><strong>No big O notations of the time complexity of the Shell sort (Knuth sequence) algorithm needed - as the complexity is dependent on the size of array and gap</strong></p>

<pre><code>alex@/tmp/sort$ cat 100-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    shell_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 100-main.c 100-shell_sort.c print_array.c -o shell
alex@/tmp/sort$ ./shell
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

13, 7, 96, 71, 19, 48, 99, 73, 86, 52
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_5. Cocktail shaker sort_**

---

<p>Write a function that sorts a doubly linked list of integers in ascending order using the <a href="/rltoken/bwa4mHfUbbWTB8J2OIHvpA" target="_blank" title="Cocktail shaker sort">Cocktail shaker sort</a> algorithm</p>

<p>Write in the file <code>101-O</code>, the big O notations of the time complexity of the Cocktail shaker sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 101-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * create_listint - Creates a doubly linked list from an array of integers
 *
 * @array: Array to convert to a doubly linked list
 * @size: Size of the array
 *
 * Return: Pointer to the first element of the created list. NULL on failure
 */
listint_t *create_listint(const int *array, size_t size)
{
    listint_t *list;
    listint_t *node;
    int *tmp;

    list = NULL;
    while (size--)
    {
        node = malloc(sizeof(*node));
        if (!node)
            return (NULL);
        tmp = (int *)&amp;node-&gt;n;
        *tmp = array[size];
        node-&gt;next = list;
        node-&gt;prev = NULL;
        list = node;
        if (list-&gt;next)
            list-&gt;next-&gt;prev = list;
    }
    return (list);
}

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    listint_t *list;
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    list = create_listint(array, n);
    if (!list)
        return (1);
    print_list(list);
    printf("\n");
    cocktail_sort_list(&amp;list);
    printf("\n");
    print_list(list);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 101-main.c 101-cocktail_sort_list.c print_list.c -o cocktail
alex@/tmp/sort$ ./cocktail
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

19, 48, 71, 99, 13, 52, 96, 73, 86, 7
19, 48, 71, 13, 99, 52, 96, 73, 86, 7
19, 48, 71, 13, 52, 99, 96, 73, 86, 7
19, 48, 71, 13, 52, 96, 99, 73, 86, 7
19, 48, 71, 13, 52, 96, 73, 99, 86, 7
19, 48, 71, 13, 52, 96, 73, 86, 99, 7
19, 48, 71, 13, 52, 96, 73, 86, 7, 99
19, 48, 71, 13, 52, 96, 73, 7, 86, 99
19, 48, 71, 13, 52, 96, 7, 73, 86, 99
19, 48, 71, 13, 52, 7, 96, 73, 86, 99
19, 48, 71, 13, 7, 52, 96, 73, 86, 99
19, 48, 71, 7, 13, 52, 96, 73, 86, 99
19, 48, 7, 71, 13, 52, 96, 73, 86, 99
19, 7, 48, 71, 13, 52, 96, 73, 86, 99
7, 19, 48, 71, 13, 52, 96, 73, 86, 99
7, 19, 48, 13, 71, 52, 96, 73, 86, 99
7, 19, 48, 13, 52, 71, 96, 73, 86, 99
7, 19, 48, 13, 52, 71, 73, 96, 86, 99
7, 19, 48, 13, 52, 71, 73, 86, 96, 99
7, 19, 13, 48, 52, 71, 73, 86, 96, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_6. Counting sort_**

---

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/ChcoDSCqnJHGC-qrSPEGHQ" target="_blank" title="Counting sort">Counting sort</a> algorithm</p>

<p>Write in the file <code>102-O</code>, the big O notations of the time complexity of the Counting sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 102-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    counting_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 102-main.c 102-counting_sort.c print_array.c -o counting
alex@/tmp/sort$ ./counting
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 4, 4, 4, 4, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 6, 6, 7, 7, 7, 7, 7, 7, 7, 7, 7, 7, 7, 7, 7, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 9, 9, 9, 10

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_7. Merge sort_**

---

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/8sZ3nAhd_YLNzHCgNbbf8A" target="_blank" title="Merge sort">Merge sort</a> algorithm</p>

<p>Write in the file <code>103-O</code>, the big O notations of the time complexity of the Merge sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 103-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    merge_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 103-main.c 103-merge_sort.c print_array.c -o merge
alex@/tmp/sort$ ./merge
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

Merging...
[left]: 19
[right]: 48
[Done]: 19, 48
Merging...
[left]: 71
[right]: 13
[Done]: 13, 71
Merging...
[left]: 99
[right]: 13, 71
[Done]: 13, 71, 99
Merging...
[left]: 19, 48
[right]: 13, 71, 99
[Done]: 13, 19, 48, 71, 99
Merging...
[left]: 52
[right]: 96
[Done]: 52, 96
Merging...
[left]: 86
[right]: 7
[Done]: 7, 86
Merging...
[left]: 73
[right]: 7, 86
[Done]: 7, 73, 86
Merging...
[left]: 52, 96
[right]: 7, 73, 86
[Done]: 7, 52, 73, 86, 96
Merging...
[left]: 13, 19, 48, 71, 99
[right]: 7, 52, 73, 86, 96
[Done]: 7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_8. Heap sort_**

---

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/YKYRdSdomaVkNrtNv1KS6Q" target="_blank" title="Heap sort">Heap sort</a> algorithm</p>

<p>Write in the file <code>104-O</code>, the big O notations of the time complexity of the Heap sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 104-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    heap_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 104-main.c 104-heap_sort.c print_array.c -o heap
alex@/tmp/sort$ ./heap
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

19, 48, 99, 86, 13, 52, 96, 73, 71, 7
19, 86, 99, 48, 13, 52, 96, 73, 71, 7
19, 86, 99, 73, 13, 52, 96, 48, 71, 7
99, 86, 19, 73, 13, 52, 96, 48, 71, 7
99, 86, 96, 73, 13, 52, 19, 48, 71, 7
7, 86, 96, 73, 13, 52, 19, 48, 71, 99
96, 86, 7, 73, 13, 52, 19, 48, 71, 99
96, 86, 52, 73, 13, 7, 19, 48, 71, 99
71, 86, 52, 73, 13, 7, 19, 48, 96, 99
86, 71, 52, 73, 13, 7, 19, 48, 96, 99
86, 73, 52, 71, 13, 7, 19, 48, 96, 99
48, 73, 52, 71, 13, 7, 19, 86, 96, 99
73, 48, 52, 71, 13, 7, 19, 86, 96, 99
73, 71, 52, 48, 13, 7, 19, 86, 96, 99
19, 71, 52, 48, 13, 7, 73, 86, 96, 99
71, 19, 52, 48, 13, 7, 73, 86, 96, 99
71, 48, 52, 19, 13, 7, 73, 86, 96, 99
7, 48, 52, 19, 13, 71, 73, 86, 96, 99
52, 48, 7, 19, 13, 71, 73, 86, 96, 99
13, 48, 7, 19, 52, 71, 73, 86, 96, 99
48, 13, 7, 19, 52, 71, 73, 86, 96, 99
48, 19, 7, 13, 52, 71, 73, 86, 96, 99
13, 19, 7, 48, 52, 71, 73, 86, 96, 99
19, 13, 7, 48, 52, 71, 73, 86, 96, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99
13, 7, 19, 48, 52, 71, 73, 86, 96, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_9. Radix sort_**

---

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/pBsj4j_AF_mJAgNZWmX3VQ" target="_blank" title="Radix sort">Radix sort</a> algorithm</p>

<pre><code>alex@/tmp/sort$ cat 105-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    radix_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 105-main.c 105-radix_sort.c print_array.c -o radix
alex@/tmp/sort$ ./radix
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

71, 52, 13, 73, 96, 86, 7, 48, 19, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

---


---

**_10. Bitonic sort_**

---

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/N-bjAbxm5yr4DoeIDz5lLw" target="_blank" title="Bitonic sort">Bitonic sort</a> algorithm</p>

<p>Write in the file <code>106-O</code>, the big O notations of the time complexity of the Bitonic sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 106-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {100, 93, 40, 57, 14, 58, 85, 54, 31, 56, 46, 39, 15, 26, 78, 13};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    bitonic_sort(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 106-main.c 106-bitonic_sort.c print_array.c -o bitonic
alex@/tmp/sort$ ./bitonic
100, 93, 40, 57, 14, 58, 85, 54, 31, 56, 46, 39, 15, 26, 78, 13

Merging [16/16] (UP):
100, 93, 40, 57, 14, 58, 85, 54, 31, 56, 46, 39, 15, 26, 78, 13
Merging [8/16] (UP):
100, 93, 40, 57, 14, 58, 85, 54
Merging [4/16] (UP):
100, 93, 40, 57
Merging [2/16] (UP):
100, 93
Result [2/16] (UP):
93, 100
Merging [2/16] (DOWN):
40, 57
Result [2/16] (DOWN):
57, 40
Result [4/16] (UP):
40, 57, 93, 100
Merging [4/16] (DOWN):
14, 58, 85, 54
Merging [2/16] (UP):
14, 58
Result [2/16] (UP):
14, 58
Merging [2/16] (DOWN):
85, 54
Result [2/16] (DOWN):
85, 54
Result [4/16] (DOWN):
85, 58, 54, 14
Result [8/16] (UP):
14, 40, 54, 57, 58, 85, 93, 100
Merging [8/16] (DOWN):
31, 56, 46, 39, 15, 26, 78, 13
Merging [4/16] (UP):
31, 56, 46, 39
Merging [2/16] (UP):
31, 56
Result [2/16] (UP):
31, 56
Merging [2/16] (DOWN):
46, 39
Result [2/16] (DOWN):
46, 39
Result [4/16] (UP):
31, 39, 46, 56
Merging [4/16] (DOWN):
15, 26, 78, 13
Merging [2/16] (UP):
15, 26
Result [2/16] (UP):
15, 26
Merging [2/16] (DOWN):
78, 13
Result [2/16] (DOWN):
78, 13
Result [4/16] (DOWN):
78, 26, 15, 13
Result [8/16] (DOWN):
78, 56, 46, 39, 31, 26, 15, 13
Result [16/16] (UP):
13, 14, 15, 26, 31, 39, 40, 46, 54, 56, 57, 58, 78, 85, 93, 100

13, 14, 15, 26, 31, 39, 40, 46, 54, 56, 57, 58, 78, 85, 93, 100
alex@/tmp/sort$
</code></pre>

---


---

**_11. Quick Sort - Hoare Partition scheme_**

---

<p>Write a function that sorts an array of integers in ascending order using the <a href="/rltoken/_pBTrH0Xyo4BRmQn4CtnMg" target="_blank" title="Quick sort">Quick sort</a> algorithm</p>

<p>Write in the file <code>107-O</code>, the big O notations of the time complexity of the Quick sort algorithm, with 1 notation per line:</p>

<pre><code>alex@/tmp/sort$ cat 107-main.c
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "sort.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int array[] = {19, 48, 99, 71, 13, 52, 96, 73, 86, 7};
    size_t n = sizeof(array) / sizeof(array[0]);

    print_array(array, n);
    printf("\n");
    quick_sort_hoare(array, n);
    printf("\n");
    print_array(array, n);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 107-main.c 107-quick_sort_hoare.c print_array.c -o quick
alex@/tmp/sort$ ./quick
19, 48, 99, 71, 13, 52, 96, 73, 86, 7

7, 48, 99, 71, 13, 52, 96, 73, 86, 19
7, 19, 99, 71, 13, 52, 96, 73, 86, 48
7, 19, 13, 71, 99, 52, 96, 73, 86, 48
7, 13, 19, 71, 99, 52, 96, 73, 86, 48
7, 13, 19, 48, 99, 52, 96, 73, 86, 71
7, 13, 19, 48, 71, 52, 96, 73, 86, 99
7, 13, 19, 48, 52, 71, 96, 73, 86, 99
7, 13, 19, 48, 52, 71, 86, 73, 96, 99
7, 13, 19, 48, 52, 71, 73, 86, 96, 99

7, 13, 19, 48, 52, 71, 73, 86, 96, 99
alex@/tmp/sort$
</code></pre>

<p>Another example of output:</p>

<pre><code>alex@/tmp/sort$ ./quick_2
87, 65, 28, 63, 93, 52, 39, 59, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 26, 42, 11, 16, 21, 75, 36, 71, 8, 45, 38

38, 65, 28, 63, 93, 52, 39, 59, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 26, 42, 11, 16, 21, 75, 36, 71, 8, 45, 87
38, 8, 28, 63, 93, 52, 39, 59, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 26, 42, 11, 16, 21, 75, 36, 71, 65, 45, 87
38, 8, 28, 36, 93, 52, 39, 59, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 26, 42, 11, 16, 21, 75, 63, 71, 65, 45, 87
38, 8, 28, 36, 21, 52, 39, 59, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 26, 42, 11, 16, 93, 75, 63, 71, 65, 45, 87
38, 8, 28, 36, 21, 16, 39, 59, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 26, 42, 11, 52, 93, 75, 63, 71, 65, 45, 87
38, 8, 28, 36, 21, 16, 11, 59, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 26, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
38, 8, 28, 36, 21, 16, 11, 26, 27, 30, 24, 83, 69, 62, 13, 6, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
38, 8, 28, 36, 21, 16, 11, 26, 27, 30, 24, 6, 69, 62, 13, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
38, 8, 28, 36, 21, 16, 11, 26, 27, 30, 24, 6, 13, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
13, 8, 28, 36, 21, 16, 11, 26, 27, 30, 24, 6, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
13, 8, 6, 36, 21, 16, 11, 26, 27, 30, 24, 28, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
13, 8, 6, 11, 21, 16, 36, 26, 27, 30, 24, 28, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
11, 8, 6, 13, 21, 16, 36, 26, 27, 30, 24, 28, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
6, 8, 11, 13, 21, 16, 36, 26, 27, 30, 24, 28, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
6, 8, 11, 13, 21, 16, 28, 26, 27, 30, 24, 36, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
6, 8, 11, 13, 21, 16, 28, 26, 27, 24, 30, 36, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
6, 8, 11, 13, 21, 16, 24, 26, 27, 28, 30, 36, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 69, 83, 88, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 87
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 69, 83, 87, 58, 92, 59, 42, 39, 52, 93, 75, 63, 71, 65, 45, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 69, 83, 87, 58, 45, 59, 42, 39, 52, 93, 75, 63, 71, 65, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 69, 83, 87, 58, 45, 59, 42, 39, 52, 65, 75, 63, 71, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 69, 71, 87, 58, 45, 59, 42, 39, 52, 65, 75, 63, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 69, 71, 63, 58, 45, 59, 42, 39, 52, 65, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 65, 71, 63, 58, 45, 59, 42, 39, 52, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 62, 65, 52, 63, 58, 45, 59, 42, 39, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 65, 52, 63, 58, 45, 59, 42, 62, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 62, 52, 63, 58, 45, 59, 42, 65, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 62, 52, 42, 58, 45, 59, 63, 65, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 59, 52, 42, 58, 45, 62, 63, 65, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 45, 52, 42, 58, 59, 62, 63, 65, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 45, 42, 52, 58, 59, 62, 63, 65, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 42, 45, 52, 58, 59, 62, 63, 65, 71, 69, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 42, 45, 52, 58, 59, 62, 63, 65, 69, 71, 75, 87, 83, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 42, 45, 52, 58, 59, 62, 63, 65, 69, 71, 75, 83, 87, 93, 92, 88
6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 42, 45, 52, 58, 59, 62, 63, 65, 69, 71, 75, 83, 87, 88, 92, 93

6, 8, 11, 13, 16, 21, 24, 26, 27, 28, 30, 36, 38, 39, 42, 45, 52, 58, 59, 62, 63, 65, 69, 71, 75, 83, 87, 88, 92, 93
alex@/tmp/sort$ 
</code></pre>

---


---

**_12. Dealer_**

---

<p><iframe allowfullscreen="" frameborder="0" height="315" src="https://www.youtube.com/embed/_HJlGWXzlLA" width="560"></iframe><br/>
<br/></p>

<p>Write a function that sorts a deck of cards.</p>

<pre><code>typedef enum kind_e
{
    SPADE = 0,
    HEART,
    CLUB,
    DIAMOND
} kind_t;

/**
 * struct card_s - Playing card
 *
 * @value: Value of the card
 * From "Ace" to "King"
 * @kind: Kind of the card
 */
typedef struct card_s
{
    const char *value;
    const kind_t kind;
} card_t;

/**
 * struct deck_node_s - Deck of card
 *
 * @card: Pointer to the card of the node
 * @prev: Pointer to the previous node of the list
 * @next: Pointer to the next node of the list
 */
typedef struct deck_node_s
{
    const card_t *card;
    struct deck_node_s *prev;
    struct deck_node_s *next;
} deck_node_t;
</code></pre>

<pre><code>alex@/tmp/sort$ cat 1000-main.c
#include &lt;stdlib.h&gt;
#include &lt;stdio.h&gt;
#include "deck.h"

void print_deck(const deck_node_t *deck)
{
    size_t i;
    char kinds[4] = {'S', 'H', 'C', 'D'};

    i = 0;
    while (deck)
    {
        if (i)
            printf(", ");
        printf("{%s, %c}", deck-&gt;card-&gt;value, kinds[deck-&gt;card-&gt;kind]);
        if (i == 12)
            printf("\n");
        i = (i + 1) % 13;
        deck = deck-&gt;next;
    }
}

deck_node_t *init_deck(const card_t cards[52])
{
    deck_node_t *deck;
    deck_node_t *node;
    size_t i;

    i = 52;
    deck = NULL;
    while (i--)
    {
        node = malloc(sizeof(*node));
        if (!node)
            return (NULL);
        node-&gt;card = &amp;cards[i];
        node-&gt;next = deck;
        node-&gt;prev = NULL;
        if (deck)
            deck-&gt;prev = node;
        deck = node;
    }
    return (deck);
}

int main(void)
{
    card_t cards[52] = {
        {"Jack", CLUB}, {"4", HEART}, {"3", HEART}, {"3", DIAMOND}, {"Queen", HEART}, {"5", HEART}, {"5", SPADE}, {"10", HEART}, {"6", HEART}, {"5", DIAMOND}, {"6", SPADE}, {"9", HEART}, {"7", DIAMOND}, {"Jack", SPADE}, {"Ace", DIAMOND}, {"9", CLUB}, {"Jack", DIAMOND}, {"7", SPADE}, {"King", DIAMOND}, {"10", CLUB}, {"King", SPADE}, {"8", CLUB}, {"9", SPADE}, {"6", CLUB}, {"Ace", CLUB}, {"3", SPADE}, {"8", SPADE}, {"9", DIAMOND}, {"2", HEART}, {"4", DIAMOND}, {"6", DIAMOND}, {"3", CLUB}, {"Queen", CLUB}, {"10", SPADE}, {"8", DIAMOND}, {"8", HEART}, {"Ace", SPADE}, {"Jack", HEART}, {"2", CLUB}, {"4", SPADE}, {"2", SPADE}, {"2", DIAMOND}, {"King", CLUB}, {"Queen", SPADE}, {"Queen", DIAMOND}, {"7", CLUB}, {"7", HEART}, {"5", CLUB}, {"10", DIAMOND}, {"4", CLUB}, {"King", HEART}, {"Ace", HEART},
    };
    deck_node_t *deck;

    deck = init_deck(cards);
    print_deck(deck);
    printf("\n");
    sort_deck(&amp;deck);
    printf("\n");
    print_deck(deck);
    return (0);
}
alex@/tmp/sort$ gcc -Wall -Wextra -Werror -pedantic  -std=gnu89 1000-main.c 1000-sort_deck.c -o deck
alex@/tmp/sort$ ./deck
{Jack, C}, {4, H}, {3, H}, {3, D}, {Queen, H}, {5, H}, {5, S}, {10, H}, {6, H}, {5, D}, {6, S}, {9, H}, {7, D}
{Jack, S}, {Ace, D}, {9, C}, {Jack, D}, {7, S}, {King, D}, {10, C}, {King, S}, {8, C}, {9, S}, {6, C}, {Ace, C}, {3, S}
{8, S}, {9, D}, {2, H}, {4, D}, {6, D}, {3, C}, {Queen, C}, {10, S}, {8, D}, {8, H}, {Ace, S}, {Jack, H}, {2, C}
{4, S}, {2, S}, {2, D}, {King, C}, {Queen, S}, {Queen, D}, {7, C}, {7, H}, {5, C}, {10, D}, {4, C}, {King, H}, {Ace, H}


{Ace, S}, {2, S}, {3, S}, {4, S}, {5, S}, {6, S}, {7, S}, {8, S}, {9, S}, {10, S}, {Jack, S}, {Queen, S}, {King, S}
{Ace, H}, {2, H}, {3, H}, {4, H}, {5, H}, {6, H}, {7, H}, {8, H}, {9, H}, {10, H}, {Jack, H}, {Queen, H}, {King, H}
{Ace, C}, {2, C}, {3, C}, {4, C}, {5, C}, {6, C}, {7, C}, {8, C}, {9, C}, {10, C}, {Jack, C}, {Queen, C}, {King, C}
{Ace, D}, {2, D}, {3, D}, {4, D}, {5, D}, {6, D}, {7, D}, {8, D}, {9, D}, {10, D}, {Jack, D}, {Queen, D}, {King, D}
alex@/tmp/sort$
</code></pre>

---
