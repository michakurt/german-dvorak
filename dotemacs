(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(display-time-mode t)
 '(tool-bar-mode nil))
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(default ((t (:family "Consolas" :foundry "outline" :slant normal :weight normal :height 113 :width normal)))))


(ido-mode t)
(setq ido-enable-flex-matching t) ; fuzzy matching is a must have


(display-time-mode)
(mouse-wheel-mode t)
(setq scrollbar-mode "right")

(setq global-font-lock-mode 1) ; everything should use fonts


(setq font-lock-maximum-decoration t)

(setq ediff-version-control-package 'vc)

;(iswitchb-mode 1)
;(iswitchb-toggle-case)
(defun scroll-up-one-line ()
      (interactive)
      (scroll-up 1))
(defun scroll-down-one-line ()
      (interactive)
      (scroll-down 1))

(global-set-key [(control ?.)] 'scroll-up-one-line)
(global-set-key [(control ?,)] 'scroll-down-one-line)

(global-set-key "\C-h\C-s" 'save-buffer)
(global-set-key "\C-ho" 'other-window)
(global-set-key "\C-hb" 'iswitchb-buffer)
(global-set-key [(control return)] 'plsql-compile)

(defun bja-open-line-above ()
  (interactive)
  (beginning-of-line)
  (open-line 1)
  (indent-according-to-mode))

(global-set-key [(meta o)] 'bja-open-line-above)

(defun bja-open-line-below ()
  (interactive)
  (end-of-line)
  (open-line 1)
  (next-line 1)
  (indent-according-to-mode))

(global-set-key [(control o)] 'bja-open-line-below)

(defun mk-yank-line ()
  "Copy current line in the kill ring"
  (interactive)
  (kill-ring-save (line-beginning-position)
                  (line-beginning-position 2))
  (message "Line yanked"))

(defun mk-yank-line-goto-beginning ()
  (interactive)
  (mk-yank-line)
  (beginning-of-line))

(global-set-key [(meta s)] 'mk-yank-line-goto-beginning)
(put 'scroll-left 'disabled nil)

(global-set-key [f11] 'scroll-left)
(global-set-key [f12] 'scroll-right)
(menu-bar-mode)
(scroll-bar-mode)
(setq-default indent-tabs-mode t)
(setq default-tab-width 4)
(setq tab-stop-list '(4 8 12 16 20 24 28 32 36 40 44 48 52 56 60 64 68 72 76 80))

(defun bf-pretty-print-xml-region (begin end)
  "Pretty format XML markup in region. You need to have nxml-mode
http://www.emacswiki.org/cgi-bin/wiki/NxmlMode installed to do
this.  The function inserts linebreaks to separate tags that have
nothing but whitespace between them.  It then indents the markup
by using nxml's indentation rules."
  (interactive "r")
  (save-excursion
      (nxml-mode)
      (goto-char begin)
      (while (search-forward-regexp "\>[ \\t]*\<" nil t) 
        (backward-char) (insert "\n"))
      (indent-region begin end))
    (message "Ah, much better!"))

