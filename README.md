# readability
a program in c that calculates the grade level

#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string s = get_string("Text: ");

    int total_letters = 0;

    for (int i = 0, n = strlen(s); i < n; i++)
    {
        if (isalpha(s[i]))
        {
            total_letters++;
        }
    }
    printf("Letters: %i\n", total_letters);

    int total_words = 1;

    for (int i = 0, n = strlen(s); i < n; i++)
    {
        if (isspace(s[i]))
        {
            total_words++;
        }
    }
    printf("Words: %i\n", total_words);

    int total_sentences = 0;

    for (int i = 0; s[i] != '\0'; i++)
    {
        if (s[i] == '.')
        {
            total_sentences++;
        }
        else if (s[i] == '!')
        {
            total_sentences++;
        }
        else if (s[i] == '?')
        {
            total_sentences++;
        }
    }
    printf("Sentences: %i\n", total_sentences);

    float L = ((total_letters / (float) total_words) * 100);
    float S = ((total_sentences / (float) total_words) * 100);

    float index = 0.0588 * L - 0.296 * S - 15.8;

    if (index < 1)
    {
        printf("Before Grade 1\n");
    }
    else if (index >= 16)
    {
        printf("Grade 16+\n");
    }
    else
    {
        printf("Grade %.0f\n", index);
    }
}
