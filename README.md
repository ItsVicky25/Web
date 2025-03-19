Here's the GitHub-friendly README.md file with proper Markdown formatting.


---

LEX Programs for Compiler Design Lab

This repository contains multiple LEX programs for lexical analysis tasks, such as counting characters, identifying tokens, and tokenizing C/C++ code fragments.


---

📜 Programs Included

1. Count Lines, Spaces, Tabs, Meta Characters, and Other Characters


2. Identify and Print Valid Identifiers


3. Identify and Print Integer and Float Values


4. Tokenize and Print Operators, Separators, Keywords, and Identifiers


5. Count and Print Total Characters, Words, and White Spaces




---

🚀 How to Compile and Run the LEX Programs

1. Install LEX & YACC (if not already installed):

sudo apt-get install flex bison  # For Linux


2. Clone this repository:

git clone https://github.com/yourusername/LEX-Programs.git
cd LEX-Programs


3. Compile and execute any LEX file:

lex filename.l
gcc lex.yy.c -o output -ll
./output




---

📌 1. Count Lines, Spaces, Tabs, Meta Characters, and Other Characters

%{
#include <stdio.h>

int line_count = 0, space_count = 0, tab_count = 0, meta_count = 0, other_count = 0;
%}

%%
\n       { line_count++; }
" "      { space_count++; }
"\t"     { tab_count++; }
[!@#$%^&*()_+={}:;"'<>,.?/~] { meta_count++; }
.        { other_count++; }
%%

int main() {
    yylex();
    printf("Lines: %d\nSpaces: %d\nTabs: %d\nMeta Characters: %d\nOther Characters: %d\n",
            line_count, space_count, tab_count, meta_count, other_count);
    return 0;
}

int yywrap() { return 1; }


---

📌 2. Identify and Print Valid C/C++ Identifiers

%{
#include <stdio.h>
%}

%%
[a-zA-Z_][a-zA-Z0-9_]* { printf("Valid Identifier: %s\n", yytext); }
.                       { /* Ignore other characters */ }

%%

int main() {
    yylex();
    return 0;
}

int yywrap() { return 1; }


---

📌 3. Identify and Print Integer and Float Values

%{
#include <stdio.h>
%}

%%
[0-9]+                  { printf("Integer: %s\n", yytext); }
[0-9]*\.[0-9]+          { printf("Float: %s\n", yytext); }
.                       { /* Ignore other characters */ }

%%

int main() {
    yylex();
    return 0;
}

int yywrap() { return 1; }


---

📌 4. Tokenize and Print Operators, Separators, Keywords, and Identifiers

%{
#include <stdio.h>
%}

KEYWORDS "int"|"float"|"return"|"if"|"else"|"while"|"for"|"do"|"switch"|"case"|"break"|"continue"|"char"|"double"|"void"
OPERATORS "+"|"-"|"*"|"/"|"="|"=="|"!="|"<"|">"|"<="|">="
SEPARATORS ";"|","|"("|")"|"{"|"}"|"["|"]"

%%
{KEYWORDS}   { printf("Keyword: %s\n", yytext); }
{OPERATORS}  { printf("Operator: %s\n", yytext); }
{SEPARATORS} { printf("Separator: %s\n", yytext); }
[a-zA-Z_][a-zA-Z0-9_]* { printf("Identifier: %s\n", yytext); }
.                      { /* Ignore other characters */ }

%%

int main() {
    yylex();
    return 0;
}

int yywrap() { return 1; }


---

📌 5. Count and Print Total Characters, Words, and White Spaces

%{
#include <stdio.h>

int char_count = 0, word_count = 0, space_count = 0;
%}

%%
[^\n\t ]+  { word_count++; char_count += yyleng; }
[ \t]      { space_count++; char_count++; }
\n         { char_count++; }
.          { char_count++; }

%%

int main() {
    yylex();
    printf("Characters: %d\nWords: %d\nWhite Spaces: %d\n", char_count, word_count, space_count);
    return 0;
}

int yywrap() { return 1; }


---

❗ Exhausted Command Handling

Each LEX program includes:

int yywrap() { return 1; }

If an "input buffer exhausted" error occurs, use:

ulimit -s unlimited

or increase buffer size in LEX.


---

📩 Contributing

Feel free to submit issues or pull requests for improvements.

📌 License: MIT
🔗 Author: Your Name

This README.md file is GitHub-formatted and includes:

Markdown headers

Code blocks

Installation steps

Execution commands

Properly formatted LEX code snippets


Let me know if you need modifications! 🚀

