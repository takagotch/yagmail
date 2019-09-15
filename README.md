### yagmail
---
https://github.com/kootenpv/yagmail


```py
// tests/all_test.py
import itertools
from yagmail import SMTP
from yagmail import raw, inline

def get_combinations(yag):
  """ """
  tos = (None, (yag.user), [yag.user, yag.user], {yag.usere: 'me', yag.user + '1': 'me'})
  subjects = ('subj', ['subj'], ['subj', 'subj1'])
  contents = (
    None,
    ['body'],
    ['body', 'body1', '<h2><center>Text</center></h2>', u"<h1>\u2013</h1>"],
    [raw("body")],
  )
  results = []
  for row in itertools.product(tos, subjects, contents):
    options = {y: z for y, z in zip(['to', 'subject', 'contents'], row)}
    options['preview_only'] = True
    results.append(options)
  
  return results
  
def test_one():
  """ """
  yag = SMTP(smtp_skip_login=True, soft_email_validation=False)
  mail_combinations = get_combinations(yag)
  for combination in mail_combinations:
    print(yag.send(**combination))
```

```
```

```
```
