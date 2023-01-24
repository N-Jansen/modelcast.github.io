## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/N-Jansen/modelcast.github.io/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List
- Test

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).  

Some SysML v2 model:
```
part def Table {
  part top : TableTop;
  part leg : Leg[4];
}
```  

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/N-Jansen/modelcast.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

```json
{
  "test": "test",
  "test": "test",
  "test": 25
}
```

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.

### **Extension** forms in a  component grammar
A component grammar is meant for extension. MontiCore therefore provides five(!) 
  mechanisms that can be used when a sub-grammar shall extend a super-grammar.
  The solutions are briefly discussed here:
1. Interface in the super-grammar
   * Introduce an interface and allow building of sub-nonterminals in sub-grammars.
      ```
      component grammar A {  
        interface X;
        N = "bla" X "blubb";
      }
      grammar B extends A {
        Y implements X = "specific" "thing"
      }
      ```
   * Advantage: Multiple extensions are possible at the same time.
             An NT `Y` can also implement multiple interfaces (like in Java). 
   * Disadvantage: the designer of `A` explicitly has to design the *hole* 
   (extension point) `X` and add it into the production.
2. Overriding (empty) nonterminal from the super-grammar
   * Use a normal nonterminal `X` and override it in a sub-grammar.
     ```
     component grammar A {  
       X = "";
       N = "bla" X "blubb";
     }
     grammar B extends A {
       @Override
       X = "my" "thing";
     }
     ```
