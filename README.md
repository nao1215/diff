[![LinuxUnitTest](https://github.com/go-spectest/difflib/actions/workflows/linux_test.yml/badge.svg)](https://github.com/go-spectest/difflib/actions/workflows/linux_test.yml)
[![MacUnitTest](https://github.com/go-spectest/difflib/actions/workflows/mac_test.yml/badge.svg)](https://github.com/go-spectest/difflib/actions/workflows/mac_test.yml)
[![WindowsUnitTest](https://github.com/go-spectest/difflib/actions/workflows/windows_test.yml/badge.svg)](https://github.com/go-spectest/difflib/actions/workflows/windows_test.yml)
[![Vuluncheck](https://github.com/go-spectest/difflib/actions/workflows/govulncheck.yml/badge.svg)](https://github.com/go-spectest/difflib/actions/workflows/govulncheck.yml)
[![reviewdog](https://github.com/go-spectest/difflib/actions/workflows/reviewdog.yml/badge.svg)](https://github.com/go-spectest/difflib/actions/workflows/reviewdog.yml)
## difflib

This repository is forked from [pmezard/go-difflib](https://github.com/pmezard/go-difflib) by [Stein Fletcher](https://github.com/steinfletcher). He was maintaining difflib within the apitest package.
  
When I forked the apitest package as the spectest package, I moved the difflib package to a separate repository. I do not have the intention to extend the functionality of difflib, but I will maintain it while maintaining the spectest package.


## What is difflib ?
The difflib is a partial port of python 3 difflib package. Its main goal was to make unified and context diff available in pure Go, mostly for testing purposes.

The following class and functions (and related tests) have be ported:

* `SequenceMatcher`
* `unified_diff()`
* `context_diff()`

## Installation

```bash
$ go get github.com/go-spectest/difflib
```

## Supported OS
- Linux
- macOS
- Windows

### Quick Start

Diffs are configured with Unified (or ContextDiff) structures, and can be output to an io.Writer or returned as a string.

```Go
diff := difflib.UnifiedDiff{
    A:        difflib.SplitLines("foo\nbar\n"),
    B:        difflib.SplitLines("foo\nbaz\n"),
    FromFile: "Original",
    ToFile:   "Current",
    Context:  3,
}
text, _ := difflib.GetUnifiedDiffString(diff)
fmt.Printf(text)
```

would output:

```
--- Original
+++ Current
@@ -1,3 +1,3 @@
 foo
-bar
+baz
```

## LICENSE
3 clause BSD license. See LICENSE file for details.