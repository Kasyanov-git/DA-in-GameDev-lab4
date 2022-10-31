# Доработка интерактивного приложения и его подготовка к сборке
Отчет по лабораторной работе #4 выполнил:
- Касьянов Никита Андреевич
- ХИ41
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Задание 2.
- Задание 3.
- Выводы.
- ✨Magic ✨

## Цель работы
 Подготовить разрабатываемое интерактивное приложение к сборке и публикации.
## Задание 1
### По теме видео практических работ 1-5 повторить реализацию игры на Unity. Привести описание выполненных действий.
Ход работы:
  - Просмотрев видеоматериалы, я повторил последовательность действий, и создал стартовую сцену игры, с оригинальным дизайном и функциональными кнопками.[[1]](https://github.com/Kasyanov-git/DA-in-GameDev-lab4/blob/main/1.jpg)
  - Создал функцию остановки игры, т.е. переход в режим паузы. [[2]](https://github.com/Kasyanov-git/DA-in-GameDev-lab4/blob/main/2.jpg)
  - Добавил Аудиосопровождение сцен, используя готовые примеры из Asset Store. [[3]](https://github.com/Kasyanov-git/DA-in-GameDev-lab4/blob/main/3.jpg)
  - добавил готовую модель героя и его анимацию в игровую сцену. [[4]](https://github.com/Kasyanov-git/DA-in-GameDev-lab4/blob/main/4.jpg)
    
  
## Задание 2
  - Ход работы.
    - Изучив то, как происходит сборка Unity проекта под другие платформы, могу сделать выводы в чём отличия этих сборок.
    - Сборка для компьютеров должна содержать исполнительный .exe файл, который будет запускать игру.
    - Для установки игры на Андройд платформы необходим APK-файл, который как-бы расспаковывает игру на платформе.
    - Так же, для каждой платформы необзодимо указывать настройки операционной системы, их разрядность, архитектуру, разрешение экрана, звуковые настройки.


## Задание 3
  - Ход работы.
    - В игровое меню был добавлен объект Slider, для которого был написан скрипт, объявляющий показатель данного слайдера аргументом громкости аудиодорожки. Таким образом, Аудио-компонент, хранящий в себе переменную громкости, просто считывает этот показатель с ползунка и передаёт на динамики. [[5]](https://github.com/Kasyanov-git/DA-in-GameDev-lab4/blob/main/5.jpg)
    ```c#
      private AudioSource audioSrc;
      private float musicVolume = 1f;
      // Start is called before the first frame update
      void Start()
      {
          audioSrc = GetComponent<AudioSource>();
      }

      // Update is called once per frame
      void Update()
      {
          audioSrc.volume = musicVolume;
      }

      public void SetVolume(float vol)
      {
          musicVolume = vol;
      }
    ```

## Выводы

Абзац умных слов о том, что было сделано и что было узнано.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
