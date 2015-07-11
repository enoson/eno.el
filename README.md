# eno.el
ace-jump/easymotion provides "goto certain char in view", which let us moving without mouse, but it's still not efficient or intuitive enough, so I create this package to "goto/copy/cut.. certain symbol/paren/l
ine.. in view".

# word
![image](https://cloud.githubusercontent.com/assets/13136462/8632037/c4f7c644-27bb-11e5-8bf3-a913cde94db9.png)

# symbol
![image](https://cloud.githubusercontent.com/assets/13136462/8632057/fc8e1170-27bc-11e5-8e14-2b52411f5f59.png)

# string
![image](https://cloud.githubusercontent.com/assets/13136462/8632065/65861e0c-27bd-11e5-8fd5-7b44f58d2129.png)

# line
![image](https://cloud.githubusercontent.com/assets/13136462/8632068/94f84c82-27bd-11e5-8b8c-23005d2e4680.png)

# paren - (), [], {}
![image](https://cloud.githubusercontent.com/assets/13136462/8632069/afdfdec0-27bd-11e5-8288-d7bf8d7c22e8.png)

# default config / customization
- `(eno-set-all-letter-str "e trinaodsuh(k[lgm,bpcyfvwjqz")`

letters used for generating hints

for qwerty: `(eno-set-all-letter-str " sdfjkla;weioqpruvncmghxz,./")`

- `(eno-set-same-finger-list '("(aq" "dtb" "sr," "lmjv" "gwpc" "uiy" "hnf" "koz["))`

list of same finger letters, e.g. if you set it as '("qa" "ws"), then it won't generate the hint "qa", "aq", "ws" and "sw".

for qwerty: `(eno-set-same-finger-list '("qaz" "wsx" "edc" "rfvg" "ujmhn" "ik," "ol." "p;/"))`


(NOTE: eno's hints generation algorithm is optimized for one and two letter, and doesn't support three or above letters)

- `(setq eno-stay-key-list '("<prior>" "<next>" "<wheel-up>" "<wheel-down>"))`

by default if you entered a key that's not in the all-letter-str, eno will quit and trigger the key, except the key in this list.

- `eno-hint-face`

face used for hints.

- `(defun eno (re &optional at-head aside) ...)`

you can write your own command based on eno by calling it with a regexp to match strings in view, optionally passing the arguments to specify whether the hint should appear at head and whether appear aside the matching strings.

# sample keybinding config
```
(require 'eno)
(require 'bind-key)
(bind-keys
  ("M-S-a". eno-word-jump)
  ("M-S-b". eno-word-copy)
  ("M-S-c". eno-word-cut)
  ("M-S-d". eno-word-paste)
  ("M-S-e". eno-symbol-jump)
  ("M-S-f". eno-symbol-copy)
  ("M-S-g". eno-symbol-cut)
  ("M-S-h". eno-symbol-paste)
  ("M-S-i". eno-str-jump)
  ("M-S-j". eno-str-copy)
  ("M-S-k". eno-str-cut)
  ("M-S-i". eno-str-paste)
  ("M-S-m". eno-line-jump)
  ("M-S-n". eno-line-copy)
  ("M-S-o". eno-line-cut)
  ("M-S-p". eno-line-paste)
  ("M-S-q". eno-paren-jump)
  ("M-S-r". eno-paren-copy)
  ("M-S-s". eno-paren-cut)
  ("M-S-t". eno-paren-paste)
  ("H-S-a". eno-symbol-copy-to)
  ("H-S-b". eno-symbol-cut-to)
  ("H-S-c". eno-symbol-paste-to)
  ("H-S-d". eno-line-copy-to)
  ("H-S-e". eno-line-cut-to)
  ("H-S-f". eno-line-paste-to)
  ("H-S-g". eno-line-comment-to)
  ("H-S-h". eno-symbol-copy-from-to)
  ("H-S-i". eno-symbol-cut-from-to)
  ("H-S-j". eno-symbol-paste-from-to)
  ("H-S-k". eno-line-copy-from-to)
  ("H-S-l". eno-line-cut-from-to)
  ("H-S-m". eno-line-paste-from-to)
  ("H-S-n". eno-line-comment-from-to))
  ("H-S-o". eno-word-goto-inline)
  ("H-S-p". eno-word-copy-to-inline)
  ("H-S-q". eno-word-cut-to-inline)
  ("H-S-r". eno-word-paste-to-inline)
  ("H-S-s". eno-url-open)
  ("H-S-t". eno-clear-overlay)

```
