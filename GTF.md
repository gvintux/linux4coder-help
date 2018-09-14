# linux4coder help GTF

Google Test Framework is a test framework for C/C++ programs

## Basic concepts

The key concept in GTF is *assertion*. assertion is an expression which result can be success, nonfatal failure and fatal failure. Fatal failure causes test termination, otherwise test continues

The *test* is a set of statements. Moreover, tests can be grouped into *test cases*

Combined test cases is a *test program*

## Assertion

Assertions which are generating, in case of their falsity, critical failures begin with `ASSERT_`, non-critical ones with `EXPECT_`. It should be noticed that critical failure performs immediate return from the function in which rejection was occurred. If after that statement follows any cleaning code you can get memory leak

There are the following statements:

logical

* ASSERT_TRUE(condition)

* ASSERT_FALSE(condition)

Comparison

* ASSERT_EQ(expect, actual) ==

* ASSERT_NE(val1, val2) !=

* ASSERT_LT(val1, val2) <

* ASSERT_LE(val1, val2) <=

* ASSERT_GT(val1, val2) >

* ASSERT_GE(val1, val2) >=

String comparison

* ASSERT_EQ(expect, actual) ==

* ASSERT_NE(val1, val2) !=

* ASSERT_LT(val1, val2) <

* ASSERT_LE(val1, val2) <=

* ASSERT_GT(val1, val2) >

* ASSERT_GE(val1, val2) >=

Compare strings

* ASSERT_STREQ (expected_str, actual_str)

* ASSERT_STRNE (str1, str2)

* ASSERT_STRCASEEQ (expected_str, actual_str) case insensitive

* ASSERT_STRCASENE (str1, str2) case insensitive

Exception check

* ASSERT_THROW (statement, exception_type)

* ASSERT_ANY_THROW (statement)

* ASSERT_NO_THROW (statement)


Checking predicates

* ASSERT_PREDN (pred, val1, val2, ..., valN) N <= 5

* ASSERT_PRED_FORMATN (pred_format, val1, val2, ..., valN)  works similarly to the previous one, but allows you to control the output

Comparison of numbers with a floating point

* ASSERT_FLOAT_EQ (expected, actual) inaccurate float comparison

* ASSERT_DOUBLE_EQ (expected, actual); - inaccurate double comparison

* ASSERT_NEAR (val1, val2, abs_error); - the difference between val1 and val2 does not exceed the error abs_error

Perform failure or success

* SUCCEED()

* FAIL()

* ADD_FAILURE()

* ADD_FAILURE_AT("file_path", line_number)


## Tests

To determine the test, use the macro TEST. It defines a void function in which statements can be used. As noted earlier, critical failure causes an immediate return from the function.
```code
TEST (test_case_name, test_name)
{
	ASSERT_EQ (1, 0) << "1 is not equal 0";
}
```
TEST takes 2 parameters that uniquely identify the test, the name of the test set and the name of the test. Within the same test set, the names of the tests should not coincide. If the name starts with `DISABLED_`, it means that you marked the test (test suite) as temporarily unused

You can use statements not only as part of the test, but also to call them from any function. There is only one limitation: statements that generate critical failures can not be called from non-void functions.


## Run

Having declared all the necessary tests, we can start them using the function `RUN_ALL_TESTS()`. The function can be called only once. It is desirable that the test program return the result of the function `RUN_ALL_TESTS()`, as some automatic testing tools determine the result of the test program execution on what it returns.

## Flags

Called before `RUN_ALL_TESTS()`, the `InitGoogleTest(argc, argv)` function makes your test program not just an executable file that displays test results. This is a complete application that accepts input parameters that change its behavior. As usual, the -h, --help options will give you a list of all supported parameters. I will list some of them
```code
# run all tests of the TestCaseName set except for SomeTest
./test --gtest_filter = TestCaseName. * - TestCaseName.SomeTest

#  run the testing program 1000 times and stop at the first failure
./test --gtest_repeat = 1000 --gtest_break_on_failure

# in addition to the output in std :: out, out.xml will be created - XML ​​report with the results of the test program execution
./test --gtest_output = "xml: out.xml"

# run tests in random order
./test --gtest_shuffle
```
If you use any parameters permanently, you can set the appropriate environment variable and run the executable without parameters. For example, setting the variable **GTEST_ALSO_RUN_DISABLED_TESTS** to a non-zero value is equivalent to using the flag `--gtest_also_run_disabled_tests`
