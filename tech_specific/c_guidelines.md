# Technical Guideline: C standards

This guideline defines C-specific compilation setups, memory safety practices, error handling conventions, and API communication patterns for generated courses.

---

## 1. Environment & Compilation Setup

Every C-based course must provide clear setup commands, compiler instructions, and automated build scripts.

### Setup Checklist:
- **Compiler**: Recommend GCC or Clang.
- **Build Automation**: Provide a simple `Makefile` or `CMakeLists.txt` rather than complex shell compile strings.
- **Standard Makefile Pattern**:
  ```makefile
  CC = gcc
  CFLAGS = -Wall -Wextra -std=c99 -O2
  LIBS = -lcurl
  
  all: main
  
  main: main.o
  	$(CC) $(CFLAGS) -o main main.o $(LIBS)
  
  main.o: main.c
  	$(CC) $(CFLAGS) -c main.c
  
  clean:
  	rm -f *.o main
  ```

---

## 2. Coding Conventions & Memory Safety

C lacks automatic memory management and garbage collection. Therefore, code examples must show rigorous standards:
- **Null Checks**: Always verify that pointers returned by functions (especially allocation routines like `malloc()`, `calloc()`, or resource loading) are not `NULL` before dereferencing them.
- **Explicit Memory Deallocation**: Ensure every dynamically allocated buffer has a corresponding `free()` path, avoiding memory leaks.
- **Buffer Safety**: Strictly ban unsafe string manipulation functions:
  * Use `strncpy()` instead of `strcpy()`.
  * Use `snprintf()` instead of `sprintf()`.
  * Use `strncat()` instead of `strcat()`.
- **Return Code Validation**: Always check status return codes of library functions (such as API call responses or file descriptors).

---

## 3. Web & API Integration (libcurl)

Since C has no native HTTP library, API interaction examples should use `libcurl` with appropriate cleanup behaviors.

*Example (API GET Request via libcurl):*
```c
#include <stdio.h>
#include <stdlib.h>
#include <curl/curl.h>

int main(void) {
    CURL *curl;
    CURLcode res;

    // Initialize curl global state
    curl_global_init(CURL_GLOBAL_DEFAULT);
    curl = curl_easy_init();

    if(curl) {
        // Set API target URL
        curl_easy_setopt(curl, CURLOPT_URL, "https://api.github.com/repos/google/google-genai");
        
        // Provide standard User-Agent header (required by some APIs)
        struct curl_slist *headers = NULL;
        headers = curl_slist_append(headers, "User-Agent: libcurl-agent/1.0");
        curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);

        // Perform request
        res = curl_easy_perform(curl);
        
        // Check for transport errors
        if(res != CURLE_OK) {
            fprintf(stderr, "curl_easy_perform() failed: %s\n", curl_easy_strerror(res));
        }

        // Clean up request-specific memory
        curl_slist_free_all(headers);
        curl_easy_cleanup(curl);
    }

    // Clean up global state
    curl_global_cleanup();
    return 0;
}
```
