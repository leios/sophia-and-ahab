import os
from pathlib import Path
import SCons.Scanner.LaTeX

# Generating chapter configuration
AddOption(
    '--chapters',
    dest='config',
    type='string',
    default='00000000000',
    action='store',
    metavar='DIR',
    help='installation prefix',
)

c_str=GetOption('config')

# Generating dictionaries for configuration.tex
# One dictionary per module
dicts = [{ "0":"content/temp/input1.tex",
           "1":"content/temp/input2.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/chapters/07_sophia_independence/00_space_junk.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/temp/none.tex" },
         { "0":"content/temp/none.tex" },]

# Generating all latex command strings
name_array = ["COne",
              "CTwo",
              "CThree",
              "CFour",
              "CFive",
              "CSix",
              "CSeven",
              "CEight",
              "CNine",
              "CTen",
              "CEleven"]

count = 0
config_str = ("\\newcommand{{\\".format() + 
               "CSet" + 
               "}}{{".format() +
               c_str +
               "}}\n".format())

for l in c_str:
    config_str += ("\\newcommand{{\\".format() + 
                   name_array[count] + 
                   "}}{{".format() +
                   dicts[count][l] +
                   "}}\n".format())
    count += 1

f = open("content/aux/configuration.tex","w")
f.write(config_str)
f.close()

env = Environment(ENV=os.environ)
env['PDFLATEX'] = 'pdflatex'
env.AppendUnique(PDFLATEXFLAGS='-synctex=0')
env.AppendUnique(PDFLATEXFLAGS='-halt-on-error')
env.AppendUnique(PDFLATEXFLAGS='-shell-escape')

main_file = env.File('main.tex')

# Ensure all the subdocuments are in a correct dependency graph.
SCons.Scanner.LaTeX.PDFLaTeXScanner().scan_recurse(main_file)

main_pdf_output = env.PDF(target='main.pdf', source=main_file)

env.Precious(main_pdf_output)
env.Default(main_pdf_output)
