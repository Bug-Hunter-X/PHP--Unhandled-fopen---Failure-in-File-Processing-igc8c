# PHP: Unhandled fopen() Failure

This repository demonstrates a common, subtle error in PHP file handling: neglecting to check the return value of `fopen()`.  The `bug.php` file shows the erroneous code, and `bugSolution.php` provides the corrected version.

The bug arises from assuming that `fopen()` will always succeed.  If the file specified in `fopen()` doesn't exist or is inaccessible for other reasons, `fopen()` returns `false`.  Attempting to use `fclose()` on a `false` value results in a fatal error.

The solution involves checking the return value of `fopen()` and only calling `fclose()` if the file handle is a valid resource.