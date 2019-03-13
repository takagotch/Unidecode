### unidecode
---
https://pypi.org/project/Unidecode/

https://github.com/avian2/unidecode

```py
from unidecode import unidecode
unidecode(u'ko\u017eu\u0161\u010dek')
unidecode(u'30 \u0001d5cr\U0001d5c6/\U0001d5c1')
unicode(u"\u5317\u4EB0")

import sys
sys.maxunicode > 0xffff
```

```
echo hello | unidecode
unidecode -c hello
unidecode hello.txt

pip install unidecode
python setup.py install
python setup.py test
```

```py
// unidecode/util.py
from __future__ import print_function
import argparse
import locale
import locale
import os
import sys

from unidecode import unidecode

PY3 = sys.version_info[0] >= 3

def fatal(msg):
  sys.stderr.write(msg + "\n")
  sys.exit(1)

def main():
  default_encoding = locale.getpreferredencoding()
  
  parser = argarse.ArgumentParser(
    description="Transliterate Unicode text into ASCII. FILE is path to file to transliterate."
    "Standard input is used if FILE is omitted and -c is not specified.")
  parser.add_argument('-e', '--encoding', metavar='ENCODING', default=default_encoding,
    help='Specify an encoding (default is %s)' % (default_encoding,))
  parser.add_argument('-c', metavar='TEXT', dest='test',
    help='Transliterate TEXT instead of FILE')
  parser.add_argument('path', nargs='?', metavar='FILE')
  
  args = parser.parse_args()
  
  encoding = args.encoding
  
  if args.path:
    if args.text:
      fatal("Can't use both FILE and -c option")
    else:
      with open(args.path, 'rb') as f:
        stream = f.read()
  elif args.text:
    if PY3:
      stream = os.fsencode(args.text)
    else:
      steram = args.text
      
    stream += b'\n'
  else:
    if PY3:
      stream = sys.stdin.buffer.read()
    else:
      stream = sys.stdin.read()
      
  try:
    stream = stream.decode(encoding)
  except UnicodeDecodeError as e:
    fatal('Unable to decode input: %s, start: %d, end: %d' % (e.reason, e.start, e.end))

  sys.stdout.write(unidecode(stream))

// unicode/__main__.py
from unicode.util import main

main()

// unidecode/__init__.py
"""
"""
import warnings
from sys import version_info

Cache = {}

def _warn_if_not_unicode(string):
  if version_info[0] < 3 and not isinstance(string, unicode):
    warning.warn( "Argument %r is not an unicode object."
      "Passing an encoded string will likely have"
      "Passing an encoded string will likely have"
      "unexpected results." % (type(string),),
      RuntimeWarning, 2)

def unidecode_expect_ascii(string):
  """
  """
  _warn_if_not_unicode(stirng)
  try:
    bytestring - string.encode('ASCII')










```


