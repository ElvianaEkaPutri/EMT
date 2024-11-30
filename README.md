# EMT
%\documentclass[a4paper,11pt]{article}

%\usepackage[utf8]{inputenc}

%%% Inserted by Sahid (2020)
% Euler for math | Palatino for rm | Helvetica for ss | Courier for tt
\renewcommand{\rmdefault}{ppl} % rm
\linespread{1.05}        % Palatino needs more leading
\usepackage[scaled]{helvet} % ss
\usepackage{courier} % tt
%\usepackage{euler} % math
%\usepackage{eulervm} % a better implementation of the euler package (not in gwTeX)
\normalfont
\usepackage[T1]{fontenc}
%%%%%%%%%%%%%%%%%%%%
\usepackage{color}
\usepackage[pdftex]{graphicx}
\usepackage[space]{grffile}
\usepackage{enumerate}
\usepackage{array}
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{alltt}
\usepackage{framed}

\usepackage[paperwidth=21cm,paperheight=29.5cm]{geometry}

%\pagestyle{empty}

\definecolor{red}{rgb}{0.4,0.0,0.0}
\definecolor{green}{rgb}{0.0,0.3,0.0}
\definecolor{black}{rgb}{0.0,0.0,0.0}
\definecolor{blue}{rgb}{0.0,0.0,0.4}
\definecolor{shadecolor}{rgb}{0.94,0.94,0.94}

\setlength{\oddsidemargin}{-0.5cm} 
\setlength{\evensidemargin}{-0.5cm}
\setlength{\topmargin}{0cm}
\setlength{\headsep}{0cm}
\setlength{\voffset}{-1cm}
\setlength{\textwidth}{17cm}
\setlength{\textheight}{25cm}

\newenvironment{eulernotebook}{}{}

\newenvironment{eulercomment}
{\color{green}\vspace{3pt plus 3pt}\parskip=3pt plus 3pt\goodbreak}%
{\vspace{2pt}}

\newenvironment{eulerttcomment}
{\color{green}\parskip=0pt\goodbreak
\begin{alltt}}%
{\end{alltt}\vspace{2pt}}

\newenvironment{eulerprompt}
{\color{red}\vspace{1pt}%
\begin{shaded}\parskip=0pt\parsep=0pt\topsep=0pt%
\begin{alltt}\ttfamily\ignorespaces}
{\end{alltt}\end{shaded}\vspace{1pt}}

\newenvironment{eulerudf}
{\color{blue}\parskip=0pt\parsep=0pt\topsep=0pt%
\begin{alltt}\ignorespaces}
{\end{alltt}\vspace{1pt}}

\newenvironment{euleroutput}
{\color{black}\vspace{0pt}%
\parskip=0pt\parsep=0pt\topsep=0pt%
\begin{alltt}\ttfamiliy\ignorespaces}
{\end{alltt}\vspace{0pt}}

\newcommand\eulerheading[1]{%
\begin{samepage}%
\color{blue}%\pagebreak{
\Large\bf\hfill#1 %}
\\[-5pt]%
\rule{\linewidth}{1pt}\nopagebreak\vspace{6pt}%
\end{samepage}\nopagebreak}

\newcommand\eulersubheading[1]{%
\begin{samepage}%
\color{blue}\vspace{6pt plus 6pt}%\goodbreak{
\large\bf\hfill#1 %}
\\[-5pt]%
\rule{\linewidth}{1pt}\vspace{6pt}
\end{samepage}\nopagebreak}

\newlength{\eulerline}
\setlength{\eulerline}{11pt}
\newcommand\eulerimg[2]{%
\begin{center}\includegraphics[height=#1\eulerline]{#2}\end{center}}

\newenvironment{eulerformula}
{\color{green}\belowdisplayskip=3pt\belowdisplayshortskip=3pt%
\abovedisplayskip=3pt\abovedisplayshortskip=3pt}{}

\setlength\parindent{0pt}
\setlength\parskip{3pt}
