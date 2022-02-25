import os
from pathlib import Path
import SCons.Scanner.LaTeX

# Generating chapter configuration
AddOption(
    '--chapters',
    dest='config',
    type='string',
    default='0',
    action='store',
    metavar='DIR',
    help='installation prefix',
)

c_str=GetOption('config')

# Generating dictionaries for configuration.tex
# One dictionary per module
dicts = [{ "0":"content/temp/input1.tex",
           "1":"content/temp/input2.tex" }]

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
env['PDFLATEX'] = 'xelatex'
env.AppendUnique(PDFLATEXFLAGS='-synctex=0')
env.AppendUnique(PDFLATEXFLAGS='-halt-on-error')
env.AppendUnique(PDFLATEXFLAGS='-shell-escape')

main_file = env.File('check.tex')

# Ensure all the subdocuments are in a correct dependency graph.
SCons.Scanner.LaTeX.PDFLaTeXScanner().scan_recurse(main_file)

main_pdf_output = env.PDF(target='check.pdf', source=main_file)

env.Precious(main_pdf_output)
env.Default(main_pdf_output)
'''


# When runninng the report.html builder, make sure that the --ignore-error option is selected
# textidote dumps its output to the stdout, and the number of errors and warning to
# stderr. Because of this, SCons will report the number of errors reported by textidote
# as its error number and crash. The only way to prevent this is to ignore
# errors.
env.Command(target='report.html', source=tex_source, action='textidote $SOURCE > $TARGET')
env.Depends('report.html', '.textidote')
env.Depends('report.html', 'ignore_file.txt')
'''
