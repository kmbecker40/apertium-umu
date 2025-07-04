AC_PREREQ(2.52)

AC_INIT([Apertium Munsee], [0.1.0], [https://github.com/apertium/apertium-umu/issues], [apertium-umu], [https://wiki.apertium.org/wiki/Apertium-umu])
AM_INIT_AUTOMAKE
AC_PROG_AWK

PKG_CHECK_MODULES(LTTOOLBOX, lttoolbox >= 3.7.4)
PKG_CHECK_MODULES(APERTIUM, apertium >= 3.9.0)
PKG_CHECK_MODULES(HFST, hfst >= 3.16.0)
PKG_CHECK_MODULES(CG3, cg3 >= 1.4.0)
PKG_CHECK_MODULES(LEXD, lexd >= 1.3.0)

AC_ARG_ENABLE([speller], AC_HELP_STRING([--enable-speller], [Build spellchecker from morphological analyser]))

AM_CONDITIONAL([ENABLE_SPELLER], [test "x$enable_speller" = "xyes"])
AM_COND_IF([ENABLE_SPELLER], [
  PKG_CHECK_MODULES(HFSTOSPELL, hfstospell >= 0.5.3, [],
     [AC_MSG_NOTICE([You will need hfst-ospell installed to use the compiled speller])])
])

AC_ARG_ENABLE([linter], AC_HELP_STRING([--enable-linter], [Lint files when compiling]))
AM_CONDITIONAL([ENABLE_LINTER], [test "x$enable_linter" = "xyes"])

PKG_CHECK_MODULES(REGTEST, apertium-regtest >= 0.9.1, [],
   [AC_MSG_WARN([Running tests requires apertium-regtest])])

AP_MKINCLUDE

AC_CONFIG_FILES([Makefile apertium-umu.pc])
AC_OUTPUT
