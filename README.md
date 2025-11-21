/*ld -r -b binary -o q.o qlock.c && cc -w -include time.h qlock.c q.o -o q -std=c90*/
c[] = {40, 34, 44, 30}; /* bg_off fg_off bg_on fg_on */ l=9; /* left padding********/
extern char _binary_qlock_c_start[]; x, y, d[8], i, dx; f[] = {31599, 19812, 14479, \
31207, 23524, 29411, 29679, 30866, 31727, 31719, 1040}; char *s, *si; p(ch) { i = (x-
l) / 2 / (3 + 1); dx = (x - l) / 2 % 4; if (x > l-1 && i < 8 && (y-2) / 2 < 5 && dx <
3 && (f[d[i]] >> ((5 - (y - 2) / 2 - 1) *3+dx)) & 1) printf("\033[1;%d;%dm%c\033[0m",
c[2], c[3], ch); else printf("\33[%d;%dm%c", c[0], c[1], ch); if(ch == '\n'){ y += 1;
x = 0; printf("\33[0m"); } else x += 1; } gd() { time_t tm = time(NULL); struct tm *t
= localtime(&tm); d[0] = t->tm_hour / 10; d[1] = t->tm_hour % 10; d[2] = 10; d[3] = t
->tm_min /10; d[4] = t->tm_min % 10; d[5] = 10; d[6]=t->tm_sec / 10; d[7] = t->tm_sec
% 10; } main() { for (gd();; printf( "\n\033[%dA\033[%dD", y + 1, x), sleep(1), gd())
for (s = _binary_qlock_c_start, x = 0, y = 0; *s; s++) p(*s); } /********************
************************************************************************************/
