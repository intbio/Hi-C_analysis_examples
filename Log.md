# Лабораторный журнал проекта Hi-C_analysis

1. Освоены базовые принципы NextFlow. Создано несколько скриптов, иллюстрирующих возможности NextFlow, скрипты находятся на сервере Newton в [папке](https://newton.bioeng.ru/jupyter/user/g_timokhin/tree/_projects/Hi-C_analysis_example/nextflow_playground)
2. Начат сбор данных Hi-C и Мicro-C. Ссылки на датасеты находятся в этом репозитории, в папке [Hi-C_Data](https://github.com/intbio/Hi-C_analysis_example/tree/master/Hi-C_Data).
3. Запущен test с заменой docker на singularity, пока что на стадии изучения ошибки
```bash
Caused by:
  Cannot run program "bsub" (in directory "/home/_shared/_projects/Hi-C_analysis_example/distiller-nf/work/dc/f4ce6dd099aa79e74f700806ca36a3"): error=2, No such file or directory

Command executed:

  bsub
```

еще такая ошибка бывает
```bash
Cannot parse params file: test_project.yml
```


4. Запущен тест пайплайна nf-core/hic

в директории results сообщение об ошибке
```bash
task_id	hash	native_id	name	status	exit	submit	duration	realtime	%cpu	rss	vmem	rchar	wchar
5	87/71c667	4066	output_documentation (1)	FAILED	127	2020-03-18 11:27:15.816	1.1s	40ms	0.0%	0	0	0	0
1	ec/aeca7c	4072	get_software_versions	FAILED	127	2020-03-18 11:27:15.838	7.1s	2.3s	760.9%	69.1 MB	1.4 GB	7.9 MB	7.2 KB
```
5.Попробовал запустить дистиллер с самого начала в новой директории. Теперь он даже не может склонировать репозиторий, говорит, что того нет.



