# Execode


<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

## Installation

For common users/developers, please just run the following command the
install the package:

``` shell
pip install -e "."
```

For intended contributors, we recommend installing the package with the
`dev` extras:

``` shell
pip install -e ".[dev]"
pre-commit install
```

## API Reference

``` python
from execode import *
```

------------------------------------------------------------------------

<a
href="https://github.com/tongyx361/execode/blob/main/execode/core.py#LNone"
target="_blank" style="float:right; font-size:smaller">source</a>

### CodeExecCfg

>      CodeExecCfg (input_begin:str='```python', input_end:str='```',
>                   output_code_prefix:str='print(',
>                   output_begin:str='```output', output_end:str='```',
>                   timeout:int=5, n_call_max:int=2,
>                   trunc_len:tuple[int,int]=(50, 50), elipsis:str='...')

*Configuration for code execution.*

|                    | **Type** | **Default**                        | **Details**                                                            |
|--------------------|----------|------------------------------------|------------------------------------------------------------------------|
| input_begin        | str      | `python |  | | input_end | str |`  |                                                                        |
| output_code_prefix | str      | print(                             | Prefix of code that will be executed to display the output.            |
| output_begin       | str      | `output |  | | output_end | str |` |                                                                        |
| timeout            | int      | 5                                  | Timeout in seconds for code execution.                                 |
| n_call_max         | int      | 2                                  | The maximum number of calls to the code execution function.            |
| trunc_len          | tuple    | (50, 50)                           | The maximum lengths to truncate the output into the beginning and end. |
| elipsis            | str      | …                                  | The elipsis to use when truncating the output.                         |

------------------------------------------------------------------------

<a
href="https://github.com/tongyx361/execode/blob/main/execode/core.py#LNone"
target="_blank" style="float:right; font-size:smaller">source</a>

#### CodeExecCfg.load_from_id_or_path

>      CodeExecCfg.load_from_id_or_path (tool_config:str='python')

*Load the configuration from the ID or path.*

|             | **Type**        | **Default** | **Details**                                             |
|-------------|-----------------|-------------|---------------------------------------------------------|
| tool_config | str             | python      | ID / Path to file of the code executeion configuration. |
| **Returns** | **CodeExecCfg** |             | **The code execution configuration object.**            |

------------------------------------------------------------------------

<a
href="https://github.com/tongyx361/execode/blob/main/execode/core.py#LNone"
target="_blank" style="float:right; font-size:smaller">source</a>

#### CodeExecCfg.no_cells_todo

>      CodeExecCfg.no_cells_todo (text:str)

*Judge if there are no code cells to execute.*

------------------------------------------------------------------------

<a
href="https://github.com/tongyx361/execode/blob/main/execode/core.py#LNone"
target="_blank" style="float:right; font-size:smaller">source</a>

#### CodeExecCfg.extract_cells

>      CodeExecCfg.extract_cells (text:str)

*Extract code cells from the text.*

|             | **Type** | **Details**                          |
|-------------|----------|--------------------------------------|
| text        | str      | The text to extract code cells from. |
| **Returns** | **list** | **The extracted code cells.**        |

------------------------------------------------------------------------

<a
href="https://github.com/tongyx361/execode/blob/main/execode/core.py#LNone"
target="_blank" style="float:right; font-size:smaller">source</a>

#### CodeExecCfg.wrap_output

>      CodeExecCfg.wrap_output (output:str)

*Return `f"{self.output_begin}\n{output}\n{self.output_end}"`*

------------------------------------------------------------------------

<a
href="https://github.com/tongyx361/execode/blob/main/execode/core.py#LNone"
target="_blank" style="float:right; font-size:smaller">source</a>

### exec_cells

>      exec_cells (cells:list[str])

*Execute the code cells like a notebook and return the stdout and stderr
of the last cell. Modified from -
https://github.com/Kipok/NeMo-Skills/blob/6a909ec0974340b02a1083dce90e79bea30ecb60/nemo_skills/code_execution/sandbox.py#L168-L233 -
https://github.com/deepseek-ai/DeepSeek-Math/blob/b8b0f8ce093d80bf8e9a641e44142f06d092c305/evaluation/infer/run_tool_integrated_eval.py#L163-L180*

|             | **Type**  | **Details**                |
|-------------|-----------|----------------------------|
| cells       | list      | The code cells to execute. |
| **Returns** | **tuple** |                            |
