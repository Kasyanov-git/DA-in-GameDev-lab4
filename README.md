# Реализация интерфейса пользователя.
Отчет по лабораторной работе #3 выполнил(а):
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
Интеграция интерфейса пользователя в разрабатываемое интерактивное приложение.
## Задание 1
### По теме видео практических работ 1-5 повторить реализацию игры на Unity. Привести описание выполненных действий.
Ход работы:
  - Просмотрев видеоматериалы, я начал повторять последовательность приведённых действий
    - Написал скрипт для энергитического щита, чтобы тот двигался за счёт перемещения курсора мыши и присвоил выполнение скрипта префабу щита
     ```c#
        void Update()
        {
          Vector3 mousePos2D = Input.mousePosition;
          mousePos2D.z =-Camera.main.transform.position.z;
          Vector3 mousePos3D = Camera.main.ScreenToWorldPoint(mousePos2D);
          Vector3 pos = this.transform.position;
          pos.x = mousePos3D.x;
          this.transform.position = pos;
        }
     ```
    - Также, добавил функцию OnCollisionEnter() для энергитического щита, чтобы объекты, с тегом "Dragon Egg", при столкновении исчезали, то есть — чтобы щит ловил падающие яица.
        ```c#
            private void OnCollisionEnter(Collision coll) {
            GameObject Collided = coll.gameObject;
            if (Collided.tag == "Dragon Egg"){
              Destroy(Collided);
            }
            } 
       ```
    - Для отображения счёта пойманых яиц, был создан Canvas, в котором создано текстовое поле для вывода значений.
    - Далее, для подсчёта очков, скрипт для энергитического поля был дополнен следущими строками. Сначала идёт обращение к текстовому полю при старте сцены, а после, при столкновении с объектом Яйцо, значение текстового поля перезаписывается с увеличением на единицу.
      ```c#
            public TextMeshProUGUI scoreGT;
            void Start()
            {
             GameObject scoreGo = GameObject.Find("Score");
             scoreGT = scoreGo.GetComponent<TextMeshProUGUI>();
             scoreGT.text = "0";
            }
            ...
            ...
            ...
            private void OnCollisionEnter(Collision coll) {
            GameObject Collided = coll.gameObject;
            if (Collided.tag == "Dragon Egg"){
              Destroy(Collided);
            }
            int score = int.Parse(scoreGT.text);
            score += 1;
            scoreGT.text = score.ToString();
            }
       ```
    
    - Таким образом, сцена начала обретать элементы игрового сервиса.
    - Следущим шагом была реализация удаления всех яиц со сцены, при пропуске щитом любого яйца, тоесть некоторая перезагрузка уровня. Было это реализовано с помощью данных строк:
      ```c#
            public void DragonEggDestroyed(){
            GameObject[] tDragonEggArray = GameObject.FindGameObjectsWithTag("Dragon Egg");
            foreach (GameObject tGO in tDragonEggArray){
                Destroy(tGO);
            }
            
       ```
  
## Задание 2
  - Ход работы.
    - По материалам видео, в основной скрипт игры была добавлена реализация потери жизней, при которой удалялся вершний слой энергитического щита. Также, при исчезновении последнего щита, сцена перезапускается.
      ```c#
            public void DragonEggDestroyed(){
            int shieldIndex = shieldList.Count - 1;
            GameObject tShieldGo = shieldList[shieldIndex];
            shieldList.RemoveAt(shieldIndex);
            Destroy(tShieldGo);
            if (shieldList.Count == 0){
                SceneManager.LoadScene("0_Scene");
            }
            }
       ```
    - Следущим на очереди было украшение сцены. Мной был найден ассет Snow_Mountain, из которого я установил на сцену заснеженную гору и окружение.[[1]](https://github.com/Kasyanov-git/DA-in-GameDev-lab3/blob/main/1.jpg)
    - Затем, по рекомендациям из видео, была произведена сортировка файлов игры по папкам и удаление ненужных файлов подключённых пакетов.[[2]](https://github.com/Kasyanov-git/DA-in-GameDev-lab3/blob/main/2.jpg)

## Задание 3
   - Ход работы.
      - По материалам видео, была произведена настройка билда для публикации именно для Яндекс Игр.
      - Был найден, скачан и добавлен в проект пакет PluginYG, для упрощения интеграции Яндекс SDK в проект [[3]](https://github.com/Kasyanov-git/DA-in-GameDev-lab3/blob/main/3.jpg)
      - Проект был сбилден, заархивирован и добавлен как черновик во вкладке Добавление сервиса в Яндекс Игры.Консоль. [[4]](https://github.com/Kasyanov-git/DA-in-GameDev-lab3/blob/main/4.jpg)
      - После прохождения модерации и выставления необходимых настроек, проект был удачно запущен с поддержкой сервиса на ПК и в браузере смартфона. [[5]](https://github.com/Kasyanov-git/DA-in-GameDev-lab3/blob/main/5.jpg) 


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
