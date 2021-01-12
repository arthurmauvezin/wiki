Find here a really useful Vim cheatsheet

??? info "Click to expand cheatsheet"
    ```bash
    +----
    | emacs-stamp: Time-stamp: <2006-11-07 23:40:22 karl>
    | vim-stamp: Latest change: Wed Apr 20 14:27:38 CEST 2011
    | .... whichever comes last *ggg*
    |
    | Title:   vim7-emacs21-cheatsheet of freezing hell
    |          ... tries to combine the two editors of choice
    |
    | Author:  Karl Voit
    | Purpose: learning emacs21 _and_ vim (for myself)
    | License: Creative Commons http://creativecommons.org/licenses/by/2.5/
    | Status:  constantly modified, updated, and expanded
    +----
    
    Alternative cheatsheets: 
      - http://www.elmindreda.org/emacs.html
      - http://hyperpolyglot.org/text-mode-editors
    
    ================================================================================
    Editor shortcuts: Emacs and vim       vim                   emacs
    ================================================================================
    
    exit                                  :q                    C-x C-c
    save                                  :w    :w!             C-x C-s
    save as                               :w 
    
    save and exit                         :wq         (or: ZZ)  C-x C-s C-x C-c
    exit without saving                   :q!         (or: ZQ)
    
    stop executing things                 ESC  or  C-c          C-g
    
    open file                             :e(dit) file          C-x C-f     (find-file)
    open file read only                                         C-x C-r     
    re-read file (discard changes)        :e(dit)!
    locate file                                                 M-x locate(-with-filter)
    
    edit file under cursor                gf       (goto file)
    
    undo last changes                     u          (or: C-_)  C-_   or   C-\
    undo one change                       :u(ndo)               C-x u
    undo latest changes on current line   U
    redo                                  C-r
    undo changes since last save                                M-x revert-buffer
    
    repeat last change                    .
    
    append text after cursor              a
    append text after EOL                 A
    
    insert text after cursor              i
    insert text before first non-whitesp. I
    insert file content                   :r file               C-x i
    
    insert line below cursor and insert   o
    insert line above cursor and insert   O
    
    join current line and next line       J
    
    mark char begin                       v  (column: C-v|C-q)  C-Space
    mark paragraph                                              M-h
    mark line begin                       V
    
    restore last selection                gv
    
    copy marked part                      y          "yank"     M-w
    copy current line                     yy           (or: Y)  
    
    paste marked part                     p                     C-y           "yank"
    paste 2nd last content                                      C-y M-y
    paste 3re last content                                      C-y M-y M-y
    
    cut marked part                       c                     C-w
    cut current line                                            C-S-Backspace
    delete marked part                    d
    
    delete char                           x                     C-d  or  DEL
    delete line                           dd     (or: :d)  C-S-Backspace
    delete to end of word                 cw     (change word)  M-d
    delete current word                   caw
    delete to EOL                         D                     C-k
    delete sentence                                             M-k
    delete paragraph                                            M-x kill-paragraph
    
    delete previous character                                   Backspace
    delete previous word                  C-w                   M-Del
    delete previous sentence                                    C-x Del
    delete previous paragraph                                   M-x backward-kill-paragraph
    
    toggle overwrite/insert mode          INS          (or: R)  M-x overwrite-mode
    replace current char with       r
    
    repeat  X times                  X                C-u X 
    
    complete word                                               M-/
    complete word backward                C-P                   M-/
    complete word forward                 C-N                   M-/
    
    cancel                                C-c                   C-g
    
    redraw                                C-l
    
    file info                             C-g
    file info (verbose)                   g C-g
    
    set auto indent                       :set ai               M-x auto-fill-mode
    				      :set textwidth=0
    
    execute shell code               :r(ead) ! 
    
    show whitespaces                      :set list
    
    insert                          :r(ead)         M-x insert-file
    
    show document statistics such as
    # columns/lines/word/characters/bytes g C-g
    
    --------------------------------------------------------------------------- Help
    
    show help of cmd XY                   :help XY
    show man-page of current word         K
    grep help                             :helpg foobar
    
    ------------------------------------------------------------------------ Buffers
    
    close buffer                          C-w c    :clo(se)     C-x k
    close buffer and return to previous                         C-x 0
    close all buffers but current         C-w o    :on(ly)      M-x kill-some-buffers
    enlarge current buffer                                      C-x 1
    
    open file for writing                                       C-x C-f
    open file for reading                                       C-x C-r
    
    change to previous buffer             C-^      C-6          C-x b
    change to buffer  number <12>     <12> C-^   <12> C-6   C-x b 
    				      :b <12>
    split vertically                      C-w s    :sp(lit)
    split horizontally                    C-w v    :vs(split)
    
    duplicate buffer                      :new
    
    change to (upper) high buffer         C-w h
    change to lower buffer                C-w l
    
    list buffers                          :ls
    
    edit in new tab                       :tabe(dit) fileA
    change to next tab                    gt
    change to previous tab                gT
    
    
    --------------------------------------------------------------------- Navigation
    
    goto line <12>                        <12>G                 M-x goto-line <12>
    
    			up                k                    C-p
    Cursor movements   left    right      h     l               C-f   C-f
    		       down             j                      C-n
    
    buffer begin                          1G       gg           M-<
    buffer end                            G                     M->
    
    line begin ... end                    0 ... $               C-a ... C-e
    line begin (first non-whitespace)       ^
    
    word next                             w                     M-f
    word last                             b                     M-b
    
    sentence previous                     (                     M-a
    sentence next                         )                     M-e
    
    paragraph begin                       {                     M-{
    paragraph end                         }                     M-}
    
    goto last place                       C-o
    goto next place (if any)              C-i
    
    goto begin of last marked part        '<
    goto end of last marked part          '>
    
    page up                               C-b                   M-v
    page down                             C-f                   C-v
    
    1/2 page up                           C-u
    1/2 page down                         C-d
    
    scroll one line down (keep cursor)    C-e
    scroll one line up (keep cursor)      C-y
    
    remember position (as p)              m p                   C-x r m
    jump to position (p)                  ` p                   C-x r b
    jump to last marked position          ``
    jump to last place edited             `.
    list all marked positions             :marks
    
    place current line in the center      z.                    C-l        "locate"
    
    ------------------------------------------------------------ Search and replace
    
    current line: goto character X        fC
    current line: goto character X backw. FC
    current line: go before character X   tC
    current line: go before char. X backw.TC
    
    activate incremental search           :set incsearch
    search incremental                    (if activated) /      C-s
    search incremental backwards          (if activated) ?      C-r
    repeat search                         n                     C-s or C-r
    repeat search in other direction      N
    filter current buffer with RegEx                            M-x occur
    
    replace                               s/foo/bar(/gci)       M-%
    
    search word under cursor              *
    search word under cursor backward     #
    search local variable under cursor    gd
    search buffer variable under cursor   gD
    
    search correspondent brace/bracker/.. %
    
    unhighlight the search patterns       :noh
    
    search for regular expressions        /REG                  C-M-s
    repeat search for reg. expr.          n                     C-M-s
    search in other directory for reg.ex. N                     C-M-r
    
    ----------------------------------------------------------------------- Spelling
    
    activate spell checking               :set spell               
    change spelling dictionary            :set spelllang=de
    search for next misspelled word       ]s
    show correction proposals             z=
    add as correct word                   zg
    add as incorrect word                 zf
    
    --------------------------------------------------------------------- Formatting
    
    lowercase current word                :map l viwuW     M-l
    capitalize current word               :map c viwu~W    M-c
    uppercase current word                :map u viwUW     M-u
    toggle case of current word           :map t viw~W
    toggle case of char under cursor      ~
    
    quote text                                                  C-c C-q
    format line
    format paragraph                      gqap                  M-q
    format whole document                 gggqG
    
    shift marked lines to left            <<
    shift marked lines to right           >>
    set shiftwidth                        :set shiftwidth=4
    
    
    ------------------------------------------------------------------------- Macros
    
    begin recording (name: foo)           qfoo                  C-x (
    end recording                         q                     C-x )
    
    execute macro foo                     @foo                  C-x e
    repeat macro execution                @@
    
    edit macro                            "ap
    end edit macro
    
    save macro
    
    ------------------------------------------------------------------------ Columns
    
    mark column begin                     C-v   (Windows: C-q)  C-space
    
    set width mark to longest line        $
    
    copy column(s)                        "*y
    paste column(s)                       p                     C-x r y       "yank"
    cut column(s)                         d                     C-x r k       "kill"
    
    insert column text (foo)              (visual:) Ifoo ESC    C-x r t foo
    
    -------------------------------------------------------------- Folding / Outline
    
    hide all                              zC                    C-c C-t
    show all                              zO                    C-c C-a
    toggle hide/show all                  zi
    
    hide this                             zc                    C-c C-d
    show this                             zo                    C-c C-s
    
    goto previous                         zk                    C-c C-p
    goto next                             zj                    C-c C-n
    
    ------------------------------------------------------------- Special Characters
    
    enter carriage return                 C-q ENTER             C-q ENTER
    enter newline                         C-q C-j               C-q C-j
    enter spoiler character ^L            C-q C-l               C-q C-l
    
    ------------------------------------------------------ Compare/merge differences
    
    start file A and B in compare mode    vimdiff A B           emerge A B
    
    emacs: goto fast-mode (C-c C-c doesn't have to be used)     C-c C-c f
    emacs: goto edit-mode                                       e
    
    next difference                       ]c                    (C-c C-c) n
    previous difference                   [c                    (C-c C-c) p
    goto difference X                                           C-u X j
    
    change to left file (higher)          C-w h
    change to right file (lower)          C-w l
    
    take this version                     :[range]diffpu(t)  dp
    take other version                    :[range]diffg(et)  do
    
    take A-version                                              (C-c C-c) a
    take B-version                                              (C-c C-c) b
    
    quit without saving the merge                               C-]
    recenter buffers                                            l
    
    emacs: http://www.cs.cmu.edu/cgi-bin/info2www?(emacs)Merge%20Commands
    
    ---------------------------------------------------------------- Version Systems
    
    vim: install vcsnursery from http://www.vim.org/scripts/script.php?script_id=1898
    
    commit changes                        :VCSCommit            C-x v v
    show differences between versions     :VCSVimDiff           C-x v =
    show log of current file              :VCSLog               C-x v l
    revert changes to most recent version :VCSRevert            C-x v u
    update current file from repos        :VCSUpdate
    
    add file to repos                     :VCSAdd               C-x v i
    show annotations                      :VCSAnnotate
    delete file (incl. from repos)        :VCSDelete
    show difference to previous version   :VCSDiff
    view a certain version                :VCSReview 42         C-x v r
    show detailed infos                   :VCSStatus
    
    ================================================================================
    Emacs specific shortcuts:
    ================================================================================
    
    execute single ELISP command:           M-: cmd
    increase font size                      C-x C-+
    decrease font size                      C-x C--
    
    M-: (info "(elisp) Key Binding Conventions")
        C-c LETTER ... (only) prefix reserved to user commands
        F5..F9     ... also reserved to user commands
    
    remove/delete trailing whitespace       M-x delete-trailing-whitespace
    
    interactively build and test regular expressions: M-x re-builder
    
    insert Unicode character (UTF-8): C-x 8   (ucs-insert)
    
    move between top, bottom, middle of window: M-r   (move-to-window-line-top-bottom)
    
    count lines/characters in region:  M-=
    
    ================================================================================
    vim specific shortcuts:
    ================================================================================
    
    
    ================================================================================
    Own vim macros
    ================================================================================
    
    " move line before boxquote into title field of boxquote
    map ,vkbqt kDj6lp0
    
    " remove/delete trailing whitespace:
      nmap ;tr :%s/\s\+$//
      vmap ;tr  :s/\s\+$//
    
    "kill quoted sig
    map ,kqs G?^> -- $d}
    
    " change subject (Subjectaenderung) (Source: Michael Prokop)
    map ,vkcs :set nohlsearch
        \:1,/^Subject: /g//s/^\(Subject: \)\(Re: \)\=\(.*\)$/
        \\1 (was: \3)/9i
    
    " simple quote (insert quote after this line)
    map ,vksq 0jikki
    
    " quote between line (insert quote in between the line)
    map ,vkqbl i0kxkkxjxi
    
    " update timestamp (make sure that "set paste" is NOT set
    iab Tue Jul 31 13:03:52 CEST 2007 =strftime("%a %b %d %T %Z %Y")
    "  map ,L  1G/Latest change:\s*/e+1CYDATE
    map ,L  1G/Latest change:\s*/e CYDATE
    
    " voit 20070306:
    " ESC-c ... capitalize current word (and goto next word)
    map c viwu~W
    " ESC-l ... lowercase current word (and goto next word)
    map l viwuW
    " ESC-u ... uppercase current word (and goto next word)
    map u viwUW
    
    
    
    FIXXME: Bereichsangaben
    
    " Using (g)vim to colorize sourcecode (from: http://barnson.org/node/295#comment-26758)
    " used here: Visual Basic syntax
    :cal SetSyn("vb")
    :syntax on
    :set background=light
    :runtime! syntax/2html.vim
    ggVG (to select all in this top frame)
    "+y (to copy to clipboard)
    
    
    ...................................................................
    ...................................................................
    ...................................................................
    ...................................................................
    ...................................................................
    		N O T E S   F O L L O W I N G
    ...................................................................
    ...................................................................
    ...................................................................
    ...................................................................
    ...................................................................
    
    Svens Vortrag:
    ------------------------------------------------------------------------- Suchen
    
    
    ------------------------------------------------------ Eingabe von Sonderzeichen
    
    Eingabe über ASCII-Nummer:
    ß 223  ä 228  ö 246  ü 252
    
    Zwei-Zeichen-Kombination:
    Digraph Input!  a + : -> ä
    
    automatische Einrücken (indenting)
    Clipboards/Register
    Markieren von Text
     von Position bis Position
     zeilenweise (block)
     als Rechteck -> Tabelle
    
    Zeile?  DOS/Windows, Unix, oder Mac?
    Automatische Erkennung
    Beliebige Wahl
    
    %page
    Anzeige - Grundlegend
    
    Aktuelle Position des Cursors (Lineal,ruler)
    
    %pause
    ASCII-Wert von Zeichen
    
    %pause
    Sichtbarmachung von speziellen Zeichen
     (TABs, trailing spaces)
     :set list -> schon oben drinnen
    
    %pause
    geteilte Fenster (horizontal,vertikal)
    -> TextKopieren, Vergleiche
    
    %page
    Anzeige - Fortgeschritten
    
    Syntax Coloring / Highlighting
    %pause
    Achtung: ersetzt keinen Parser!
    
    %pause
    Struktur der Datei anzeigen - Baumstruktur
    Text verstecken
    Syntax dependant
    Kommandos zum Einklappen und Verstecken
    
    %page
    Abkürzungen - Abbreviations
    
    %pause
    einfache Wortexpansion:
    LS -> Leutheuser-Schnarrenberger
    
    %pause
    mehrere Worte:
    LT -> Linux-Tag Chemnitz
    
    %pause
    mehr als nur Buchstaben:
    function_mit_viel_bedeutung(*par1,par2)
    * = neue Cursorposition
    
    %pause
    mehrzeilige Floskeln:
    
    Sehr geehrter Herr Spammer..
    ..Aufnahme ins Killfile..
    Gründe:  [Liste]
    Mit  freundlichen Grüßen
    
    %page
    Goodies
    
    Autosave
    Backup files
    Compiler
    Filtering
    Sessionfile
    Syntax Input
    
    %page
    Grenzen - Limits
    
    Endlicher Speicher -> Grenzen
    
    Dateigröße
    Dateinamenlänge
    Displaybreite
    
    Zeilenlänge
    Zeilenanzahl
    
    Bufferanzahl
    Registergröße
    
    ,----
    | 2do
    `----
    
    tabs (vim7)
    
    retab + ersetzen:
    :set tabstop=4
    :set expandtab
    :%retab
    
    ^M herauslöschen
    
    align-current
    
    
    query option value        :set OPTION?
    
    folding + examples (emacs-2do-list and vim-2do-list)
    
    mika@grml ~ % grep boxes .vimrc
    " 040420 introduced history 8-) and slightly modified 'boxes'-stuff
    " 030219 VBlockquote.vim - like the tool "boxes" works ;-)
    " 030219 Call boxes - with some funny box-styles ;o)
     map ;0 :'<,'>!boxes
     map ;1 :'<,'>!boxes -d boxquote
     map ;2 :'<,'>!boxes -d peek -a c -s 40x5
     map ;3 :'<,'>!boxes -d c-cmt
     map ;4 :'<,'>!boxes -d dog -a c
     map ;5 :'<,'>!boxes -d simple -a
    jr
     map ;6 :'<,'>!boxes -d headline
    --> Test! (FIXXME)
    --> boxes = extra-tool!
    
    "boxing" text              C-c q
    title of box               C-c w
    
    Snippets einfügen wie zB :
    :he :iabbrev
    :he mapmode-i
    (Vim7: C-x C-o)
    
    Ranges: . .+3 % ,. .,$
    
    
    .........................................................
    
    ,----
    | notes from a former talk:
    `----
    :set tw=50 ... set texxt width
    map  gqip ... macro setzen
    :set ft=html
    :set paste ... Einfuegen ohne Umformatierung
    :set nopaste ...
    :set sw ... Option vervollstaendigen lassen
    :set sw= ... Option plus Wert vervollstaendigen lassen
    :set listchars=tab:»·,trail:·,,eol:$ ... wie sollen list-Elemente usw visualisiert werden?
    :w datei:.neu ... Kopie mit Anhaengsel ".neu" erstellen, Buffer bleibt bei "datei"
    :!ls -l % ... shell-Kommando ls aufrufen (%=aktueller Buffername)
    :! ... letzter Befehl, der mit "!" begonnen hat
    C-w n ... C-w=Fensterbefehl, n=new
    C-w C-r ... unterster Buffer oben einfuegen (rotate)
    :help C-v C-w ... show help on windows-commands (C-v nur um C-w einzugeben)
    
    vimdiff
    :diffget ... Aenderungen in den Buffer uebernehmen
    
    %%% vim: ft=mgp ai noet ts=2
    
    ------------------------------------------
    Emacs und ispell:
    
    ;; User-Dictionary ohne Nachfrage speichern
    (setq ispell-silently-savep t)
    (autoload 'flyspell-mode "flyspell" "On-the-fly spelling checking" t)
    (autoload 'flyspell-mode "flyspell" "On-the-fly ispell." t)
    (setq ispell-program-name "aspell")
    
    ;; Initialize spell checking
    (setq-default ispell-program-name "aspell")
    (set-default 'ispell-change-directory "ndeutsch8-15")
    (set-default 'ispell-local-dictionary "ndeutsch8-15")
    ;; ========================
    ;; ISPELL
    ;; ========================
    (require 'ispell)
    (add-to-list 'ispell-dictionary-alist
          '("ndeutsch8-15"
    	"[a-zA-Z\304\326\334\344\366\337\374]"
    	"[^a-zA-Z\304\326\334\344\366\337\374]"
    	"[']" t
           ("-C" "-d" "german")
    	"~latin1" iso-8859-15))
    
    ;; ========================
    ;; ISPELL End
    ;; ========================
    
    ;; ========================
    ;; FLYSPELL
    ;; ========================
    (add-hook 'flyspell-mode-hook
       (function (lambda ()
    	     (setq ispell-local-dictionary "ndeutsch8-15")
    	)))
    
    
    M-X change-ispell-dictionary
    
    -----------------------------------------------------------
    emacs und LaTeX
    
    Added in file c:\.emacs
    
    (require 'tex-site)
    (setq tex-dvi-view-command "C:\texmf\miktex\bin\yap.exe")
    (custom-set-variables
      ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
      ;; Your init file should contain only one such instance.
     '(TeX-output-view-style (quote (("^dvi$" "^pstricks$\\|^pst-\\|^psfrag$" "%(o?)dvips %d -o && gv %f") ("^dvi$" "^a4\\(?:dutch\\|paper\\|wide\\)?\\|sem-a4$" "%(o?)xdvi %dS -paper a4 %d") ("^dvi$" ("^a5\\(?:comb\\|paper\\)?$" "^landscape$") "%(o?)xdvi %dS -paper a5r -s 0 %d") ("^dvi$" "^a5\\(?:comb\\|paper\\)?$" "%(o?)xdvi %dS -paper a5 %d") ("^dvi$" "^b5paper$" "%(o?)xdvi %dS -paper b5 %d") ("^dvi$" ("^landscape$" "^pstricks$\\|^psfrag$") "%(o?)dvips -t landscape %d -o && gv %f") ("^dvi$" "^letterpaper$" "%(o?)xdvi %dS -paper us %d") ("^dvi$" "^legalpaper$" "%(o?)xdvi %dS -paper legal %d") ("^dvi$" "^executivepaper$" "%(o?)xdvi %dS -paper 7.25x10.5in %d") ("^dvi$" "^landscape$" "%(o?)xdvi %dS -paper a4r -s 0 %d") ("^dvi$" "." "%(o?)xdvi %dS %d") ("^pdf$" "." "\"c:\\Programme\\Adobe\\Acrobat 6.0\\Reader\\AcroRd32.exe\" %o") ("^html?$" "." "netscape %o")))))
    (custom-set-faces
      ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
      ;; Your init file should contain only one such instance.
     )
    
    
    Change target to PDFLaTeX: C-c C-t C-p
    Compiled using C-c C-c
    
    
    C-c C-s  .... section ...
    C-c C-e  .... environments
    C-c C-f C-(b|i|...) ... bold italic
    C-c C-c  ... compile
    
    http://www.gnu.org/software/auctex/manual/reftex.html
    (require 'reftex)
    M-x reftex-mode 
    
    C-c = (reftex-toc)
    C-c ( (reftex-label)
    C-c ) (reftex-reference)
    C-c [ BibTeX
    C-c & (reftex-view-crossref)
    
    === [ ENDE ] === ------------------------------------------------------------------------------
     %%% Local Variables:
     %%% mode: outline
     %%% outline-regexp: "\\(\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\]\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\]\\(\\[.+\\]\\)? .*\\)\\|\\(^=== \\[ .* \\] ===.*\\)"
     %%% eval: (auto-fill-mode -1)
     %%% eval: (flyspell-mode -1)
     %%% eval: (end-of-buffer)
     %%% eval: (hide-body)
     %%% emerge-set-combine-versions-template: "%a\n%b\n"
     %%% End:
     %%% OLD-outline-regexp: "\\(\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\]\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\]\\(\\[\\(maggie\\|lisa\\)\\]\\)? .*\\)"
     %%% OLD-outline-regexp nur "[][] Text": "\\(\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\]\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\] .*\\)"
     %%% OLD-outline-regexp inkl. Sterne als Items: "\\(\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\]\\[\\([1-2][0-9][0-9][0-9][0-1][0-9][0-3][0-9]\\)?\\] .*\\)\\|\\(*+ \\)"
    ```
