#AM_CFLAGS = --pedantic -Wall
#-DDEBUG

if HAVE_WIDE_NCURSES
sudokun_LDADD = ${ncursesw_LIBS}
else
sudokun_LDADD = ${ncurses_LIBS}
endif
bin_PROGRAMS = sudokun
sudokun_SOURCES = main.c sudoku.c sudoku.h utils.c utils.h

if BUILD_CAIRO
sudokun_SOURCES += outp.c outp.h
AM_CFLAGS := @CAIRO_CFLAGS@
sudokun_LDADD += @CAIRO_LIBS@
endif

AM_CPPFLAGS = -DLOCALEDIR=\""$(localedir)"\"
LIBS = @LIBINTL@
