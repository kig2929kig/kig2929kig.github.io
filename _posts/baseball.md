```python
from google.colab import drive
drive.mount("/content/drive")
!jupyter nbconvert --to markdown "/content/drive/MyDrive/Colab Notebooks/baseball.ipynb"
```

    Drive already mounted at /content/drive; to attempt to forcibly remount, call drive.mount("/content/drive", force_remount=True).
    [NbConvertApp] WARNING | pattern '/content/drive/MyDrive/Colab Notebooks/baseball.ipynb' matched no files
    This application is used to convert notebook files (*.ipynb)
            to various other formats.
    
            WARNING: THE COMMANDLINE INTERFACE MAY CHANGE IN FUTURE RELEASES.
    
    Options
    =======
    The options below are convenience aliases to configurable class-options,
    as listed in the "Equivalent to" description-line of the aliases.
    To see all configurable class-options for some <cmd>, use:
        <cmd> --help-all
    
    --debug
        set log level to logging.DEBUG (maximize logging output)
        Equivalent to: [--Application.log_level=10]
    --show-config
        Show the application's configuration (human-readable format)
        Equivalent to: [--Application.show_config=True]
    --show-config-json
        Show the application's configuration (json format)
        Equivalent to: [--Application.show_config_json=True]
    --generate-config
        generate default config file
        Equivalent to: [--JupyterApp.generate_config=True]
    -y
        Answer yes to any questions instead of prompting.
        Equivalent to: [--JupyterApp.answer_yes=True]
    --execute
        Execute the notebook prior to export.
        Equivalent to: [--ExecutePreprocessor.enabled=True]
    --allow-errors
        Continue notebook execution even if one of the cells throws an error and include the error message in the cell output (the default behaviour is to abort conversion). This flag is only relevant if '--execute' was specified, too.
        Equivalent to: [--ExecutePreprocessor.allow_errors=True]
    --stdin
        read a single notebook file from stdin. Write the resulting notebook with default basename 'notebook.*'
        Equivalent to: [--NbConvertApp.from_stdin=True]
    --stdout
        Write notebook output to stdout instead of files.
        Equivalent to: [--NbConvertApp.writer_class=StdoutWriter]
    --inplace
        Run nbconvert in place, overwriting the existing notebook (only 
                relevant when converting to notebook format)
        Equivalent to: [--NbConvertApp.use_output_suffix=False --NbConvertApp.export_format=notebook --FilesWriter.build_directory=]
    --clear-output
        Clear output of current file and save in place, 
                overwriting the existing notebook.
        Equivalent to: [--NbConvertApp.use_output_suffix=False --NbConvertApp.export_format=notebook --FilesWriter.build_directory= --ClearOutputPreprocessor.enabled=True]
    --no-prompt
        Exclude input and output prompts from converted document.
        Equivalent to: [--TemplateExporter.exclude_input_prompt=True --TemplateExporter.exclude_output_prompt=True]
    --no-input
        Exclude input cells and output prompts from converted document. 
                This mode is ideal for generating code-free reports.
        Equivalent to: [--TemplateExporter.exclude_output_prompt=True --TemplateExporter.exclude_input=True]
    --log-level=<Enum>
        Set the log level by value or name.
        Choices: any of [0, 10, 20, 30, 40, 50, 'DEBUG', 'INFO', 'WARN', 'ERROR', 'CRITICAL']
        Default: 30
        Equivalent to: [--Application.log_level]
    --config=<Unicode>
        Full path of a config file.
        Default: ''
        Equivalent to: [--JupyterApp.config_file]
    --to=<Unicode>
        The export format to be used, either one of the built-in formats
                ['asciidoc', 'custom', 'html', 'latex', 'markdown', 'notebook', 'pdf', 'python', 'rst', 'script', 'slides']
                or a dotted object name that represents the import path for an
                `Exporter` class
        Default: 'html'
        Equivalent to: [--NbConvertApp.export_format]
    --template=<Unicode>
        Name of the template file to use
        Default: ''
        Equivalent to: [--TemplateExporter.template_file]
    --writer=<DottedObjectName>
        Writer class used to write the 
                                            results of the conversion
        Default: 'FilesWriter'
        Equivalent to: [--NbConvertApp.writer_class]
    --post=<DottedOrNone>
        PostProcessor class used to write the
                                            results of the conversion
        Default: ''
        Equivalent to: [--NbConvertApp.postprocessor_class]
    --output=<Unicode>
        overwrite base name use for output files.
                    can only be used when converting one notebook at a time.
        Default: ''
        Equivalent to: [--NbConvertApp.output_base]
    --output-dir=<Unicode>
        Directory to write output(s) to. Defaults
                                      to output to the directory of each notebook. To recover
                                      previous default behaviour (outputting to the current 
                                      working directory) use . as the flag value.
        Default: ''
        Equivalent to: [--FilesWriter.build_directory]
    --reveal-prefix=<Unicode>
        The URL prefix for reveal.js (version 3.x).
                This defaults to the reveal CDN, but can be any url pointing to a copy 
                of reveal.js. 
                For speaker notes to work, this must be a relative path to a local 
                copy of reveal.js: e.g., "reveal.js".
                If a relative path is given, it must be a subdirectory of the
                current directory (from which the server is run).
                See the usage documentation
                (https://nbconvert.readthedocs.io/en/latest/usage.html#reveal-js-html-slideshow)
                for more details.
        Default: ''
        Equivalent to: [--SlidesExporter.reveal_url_prefix]
    --nbformat=<Enum>
        The nbformat version to write.
                Use this to downgrade notebooks.
        Choices: any of [1, 2, 3, 4]
        Default: 4
        Equivalent to: [--NotebookExporter.nbformat_version]
    
    Examples
    --------
    
        The simplest way to use nbconvert is
    
                > jupyter nbconvert mynotebook.ipynb
    
                which will convert mynotebook.ipynb to the default format (probably HTML).
    
                You can specify the export format with `--to`.
                Options include ['asciidoc', 'custom', 'html', 'latex', 'markdown', 'notebook', 'pdf', 'python', 'rst', 'script', 'slides'].
    
                > jupyter nbconvert --to latex mynotebook.ipynb
    
                Both HTML and LaTeX support multiple output templates. LaTeX includes
                'base', 'article' and 'report'.  HTML includes 'basic' and 'full'. You
                can specify the flavor of the format used.
    
                > jupyter nbconvert --to html --template basic mynotebook.ipynb
    
                You can also pipe the output to stdout, rather than a file
    
                > jupyter nbconvert mynotebook.ipynb --stdout
    
                PDF is generated via latex
    
                > jupyter nbconvert mynotebook.ipynb --to pdf
    
                You can get (and serve) a Reveal.js-powered slideshow
    
                > jupyter nbconvert myslides.ipynb --to slides --post serve
    
                Multiple notebooks can be given at the command line in a couple of 
                different ways:
    
                > jupyter nbconvert notebook*.ipynb
                > jupyter nbconvert notebook1.ipynb notebook2.ipynb
    
                or you can specify the notebooks list in a config file, containing::
    
                    c.NbConvertApp.notebooks = ["my_notebook.ipynb"]
    
                > jupyter nbconvert --config mycfg.py
    
    To see all available configurables, use `--help-all`.
    


# 숫자 야구 게임
숫자 야구 게임은 연역적 논리 게임으로 컴퓨터가 1부터 9까지 중복되지 않은 3자리 비밀 숫자를 무작위로 뽑고, 플레이어는 3자리 비밀 숫자를 맞추는 게임입니다. 3자리 비밀 숫자 중 위치와 숫자까지 맞추면 스트라이크, 숫자만 맞추며 볼, 위치와 숫자 모두 맞추지 못했다면 노볼입니다.  

예)  

|숫자 야구 게임|||
|:------:|:---:|:---:|
|컴퓨터|123|"123"은 비밀 숫자로 플레이어는 알 수 없습니다.|
|플레이어|145|1 스트라이크|
|플레이어|415|1 볼|
|플레이어|412|2 볼|
|플레이어|321|1스트라이크, 2 볼|
|플레이어|456|노볼|

10번 안에 비밀 숫자를 맞추면(3 스트라이크) 플레이어가 이기는 게임입니다.




## 1. 비밀 숫자 만들기

[파이썬-의사 난수 생성] https://docs.python.org/ko/3/library/random.html  
- random.randint(a,b) : `a <= N <= b` 를 만족하는 임의의 정수 N을 반환합니다.


```python
import random

secret_number = random.randint(1,9)
print(secret_number)
```

    2


### 3자리 비밀 숫자를 만드는 다양한 방법
- random.sample() 사용  
random.sample(list, k) : list에 있는 목록 중 k길이의 list를 반환합니다.


```python
import random
secret_number = random.sample(range(1,10),3) # range()
#secret_number = random.sample([1,2,3,4,5,6,7,8,9], 3)
print(secret_number)
```

    [2, 9, 1]


+ in 연산자를 이용하여 리스트에 숫자가 있으면 pass하고 없다면 리스트에 추가합니다.


```python
import random
secret_number = []
while True :
  number = random.randint(1,9)
  
  if number in secret_number :
    pass
  else :
    secret_number.append(number)
  
  if len(secret_number) == 3 :
    break
  
print(secret_number)
```

    [1, 5, 4]


## 2. 플레이어가 입력한 3자리 숫자와 비밀 숫자 비교하기


```python
import random

strike = 0 # 스트라이크
ball = 0 # 볼
index = 0 # 플레이어가 입력한 3자리 숫자의 인덱스

secret_number = random.sample(range(1,10),3) # 3자리 비밀 숫자
player_number = input("추측한 숫자를 입력하세요 >> ")
print(secret_number)
for number in secret_number :
  if int(player_number[index]) == number : # 비밀 숫자와 플레이어가 입력한 숫자 비교 (스트라이크)
    strike = strike + 1
  elif int(player_number[index]) in secret_number : # in 연산자를 이용하여 비밀 숫자가 있는지 비교 (볼)
    ball = ball + 1
  index = index + 1 # 인덱스 증가

print(strike, "스트라이크", " / ", ball, "볼")
```

    추측한 숫자를 입력하세요 >> 123
    [9, 6, 7]
    0 스트라이크  /  0 볼


## 3. 숫자 야구 게임 소스코드


```python
import random

game_count = 0 # 게임 회수를 카운트
strike = 0 # 스트라이크
ball = 0 # 볼
index = 0 # 플레이어가 입력한 3자리 숫자의 인덱스

secret_number = random.sample(range(1,10),3) # 3자리 비밀 숫자

print(" >> 숫자 야구 게임 << ")
#print(secret_number)

while game_count < 10 :
  strike, ball, index = 0, 0, 0
  player_number = input("추측한 숫자를 입력하세요 >> ")
  
  for number in secret_number :
    if int(player_number[index]) == number : # 비밀 숫자와 플레이어가 입력한 숫자 비교 (스트라이크)
      strike = strike + 1
    elif int(player_number[index]) in secret_number : # in 연산자를 이용하여 비밀 숫자가 있는지 비교 (볼)
      ball = ball + 1
    
    index = index + 1 # 인덱스 증가
  
  print(strike, "스트라이크", " / ", ball, "볼")
  game_count = game_count + 1
  
  if strike == 3 :
    print("축하합니다.", game_count, "번만에 맞췄습니다.")
    break
    35
if game_count == 10 : print("게임 종료")

```

     >> 숫자 야구 게임 << 
    추측한 숫자를 입력하세요 >> 123
    0 스트라이크  /  1 볼
    추측한 숫자를 입력하세요 >> 456
    0 스트라이크  /  1 볼
    추측한 숫자를 입력하세요 >> 789
    0 스트라이크  /  1 볼
    추측한 숫자를 입력하세요 >> 234
    0 스트라이크  /  0 볼
    추측한 숫자를 입력하세요 >> 516
    2 스트라이크  /  0 볼
    추측한 숫자를 입력하세요 >> 517
    3 스트라이크  /  0 볼
    축하합니다. 6 번만에 맞췄습니다.


## 4. 추가로 생각해보기
+ 플레이어가 입력한 값이 숫자가 아니거나 똑같은 숫자를 입력하는 경우
+ 플레이어가 입력한 값의 숫자가 3자리가 아닌 경우와 숫자와 숫자 사이에 공백이 입력된 경우
+ 게임이 종료되면 다시 한번 게임을 할 것인지? 물어보고 시작하거나 종료할 수 있도록 수정
+ 소스코드를 함수로 만들어서 간결하게 만들기
