# llm-chat-code-helper
This Shell script copies all the code in the current directory into your clipboard so you can paste it into ChatGPT (or your LLM of choice) and ask it to make changes to it.

Naturally, this only works for small repositories due to token limits. If you have a big repository, you can modify this script so it only copies the most relevant files.

I created this script because I wanted to make use of GPT-4 Turbo's longer token limit to help me with a small side project. Also, I already had a ChatGPT Plus subscription so I didn't want to pay for API calls (which can be expensive when you're pasting your entire codebase into the prompt). It's an alternative to Copilot; I found GPT-4 Turbo to be much better at writing big chunks of code than Copilot.

The script in `./copy_code` is currently set up to copy all `.h`, `.c`, and `.md` files in the current folder. To use it, just paste it into one of you repos and modify it to use whatever file extensions you have in your project.

Here's an example of the output

```
File: ./src/parser.c
\`\`\`
1: #include "parser.h"
2: 
3: #include <stdbool.h>
4: 
5: #include "syntax.h"
...
\`\`\`

File: ./src/compiler.c
\`\`\`
1: #include "compiler.h"
2: 
3: #include <stdlib.h>
4: #include <string.h>
...
\`\`\`
```

After running the script, I go on ChatGPT and give it a prompt such as "I am doing \<brief description of my project\>. Add unit tests to this function `functionABC`. Here's all my code: \<paste output from script\>".

You can also use ChatGPT's "Custom Instructions" to tell the LLM to show you what lines it's changing with something like "For each file that needs to be changed, write out the changes similar to a unified diff like `diff -U0`".
