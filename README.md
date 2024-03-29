[![LinuxUnitTest](https://github.com/nao1215/diff/actions/workflows/linux_test.yml/badge.svg)](https://github.com/nao1215/diff/actions/workflows/linux_test.yml)
[![MacUnitTest](https://github.com/nao1215/diff/actions/workflows/mac_test.yml/badge.svg)](https://github.com/nao1215/diff/actions/workflows/mac_test.yml)
[![WindowsUnitTest](https://github.com/nao1215/diff/actions/workflows/windows_test.yml/badge.svg)](https://github.com/nao1215/diff/actions/workflows/windows_test.yml)
[![Vuluncheck](https://github.com/nao1215/diff/actions/workflows/govulncheck.yml/badge.svg)](https://github.com/nao1215/diff/actions/workflows/govulncheck.yml)
[![reviewdog](https://github.com/nao1215/diff/actions/workflows/reviewdog.yml/badge.svg)](https://github.com/nao1215/diff/actions/workflows/reviewdog.yml)
[![Gosec](https://github.com/nao1215/diff/actions/workflows/security.yml/badge.svg)](https://github.com/nao1215/diff/actions/workflows/security.yml)
![Coverage](https://github.com/nao1215/octocovs-central-repo/blob/main//badges/nao1215/diff/coverage.svg?raw=true)
## nao1215/diff package

This repository is forked from [pmezard/go-difflib](https://github.com/pmezard/go-difflib) by [Stein Fletcher](https://github.com/steinfletcher). He was maintaining difflib within the apitest package.
  
When I forked the apitest package as the spectest package, I moved the nao1215/diff package to a separate repository. I do not have the intention to extend the functionality of nao1215/diff, but I will maintain it while maintaining the spectest package.

The difference from the original version is that the standard output ("+++", "---" output) is colored even in the Windows environment. In other words, there is no longer any functional difference from Linux or Mac even on Windows.

## What is nao1215/diff package ?
The nao1215/diff is a partial port of python 3 difflib package. Its main goal was to make unified and context diff available in pure Go, mostly for testing purposes.

The following class and functions (and related tests) have be ported:

* `SequenceMatcher`
* `unified_diff()`
* `context_diff()`

## Installation

```bash
$ go get github.com/nao1215/diff
```

## Supported OS
- Linux
- macOS
- Windows

### Quick Start

Diffs are configured with Unified (or ContextDiff) structures, and can be output to an io.Writer or returned as a string.

```Go
diff := diff.UnifiedDiff{
    A:        diff.SplitLines("foo\nbar\n"),
    B:        diff.SplitLines("foo\nbaz\n"),
    FromFile: "Original",
    ToFile:   "Current",
    Context:  3,
}
text, _ := diff.GetUnifiedDiffString(diff)
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
