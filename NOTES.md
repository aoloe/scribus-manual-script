# Notes

## Contributing to the scripter documentation
there is an official documentation that is edited with a revision system in structured file by a few people. and a commenting system that allows everybody to easily put their comments there where they think other people will need them...
and, in a second step, the editors will go through the comments and integrate them into the "official" docs

- http://scribus-scripter.readthedocs.org/en/latest/
- https://github.com/jainbasil/scripter-doc

## Learning Python

- [A Byte of Python](http://www.swaroopch.com/notes/python/) by Swaroop C H.
- [Introduction to Programming with Python](http://opentechschool.github.io/python-beginners/en/index.html) by Open Tech School.

## The Python interpreter

### Using the system interpreter on Windows

https://wiki.scribus.net/canvas/Windows_Full_Python_Integration

## Debugging the scripts

In the forums, Juha asks: I am running python scripts in Scribus scripter. I would like to debug these scripts. I an using system default python interpreter as instructed here: https://wiki.scribus.net/canvas/Windows_Full_Python_Integration. I am using PyCharm IDE for python but the problem is that running scripter script cannot be found in PyCharm "attach to process" list. Is there any way to debug Scribus scripts?

Ale's answer:

I don't know if there is a way to do it, but I can image that there is none. (or none that is easy to activate).

What I've done in the past, is to mock the Scripter API and run the script outside of Scribus.

You can see here, how such a "Scribus" class can look like:

https://github.com/aoloe/scribus-script-repository/blob/master/typographic-grid/typographic-grid.py

during the lunch break, I'll create a "standalone" script that one import the code.

## Troubleshooting

### Replacing text content

Scribus has issues keeping the format, when replacing (or typing) text.

This code will replace the text in the current frame and set it to test without losing the formatting (as moc wants to do)

```py
scribus.selectText(0, scribus.getTextLength());
scribus.deleteText();
scribus.insertText('test', -1);
```

this code will lose the formatting

```py
scribus.deleteText();
scribus.insertText('test', -1);
```

this also lose the formatting:

```
scribus.setText('acbdefg');
```
