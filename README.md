## 1 Алгоритм генерации
Для того, чтобы генерировать поле, в котором гарантированно найдутся какие-то слова, а также чтобы впоследствии проверять слова, вводимые пользователем, необходимо подготовить несколько словарей, каждый из которых содержит различные слова, состоящие только из определенного количества букв.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/bfeac045-67d6-4953-94ff-142392262301)  

Далее, пусть имеется массив, ячейки которого представляют собой клетки игрового поля, список свободных клеток, в котором те же самые клетки хранятся последовательно, а также список для сбора текущего слова, изначально пустой.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/ca756f58-8051-49af-bd62-21a554976ec2)  

Из списка свободных клеток случайным образом выбирается клетка, удаляется оттуда и добавляется в список клеток текущего слова, а также к списку текущего слова. Затем для нее определяются возможные направления движения (вверх, вниз, влево, вправо). Из этих направлений случайным образом выбирается одно и удаляется из списка возможных. Производится проверка на то, может ли соседняя клетка по этому направлению относительно текущей стать следующей клеткой (если ей не присвоена буква), т.е. есть ли она в списке свободных клеток. Если есть, то эта клетка становится текущей и для нее повторяются все описанные выше операции.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/32cba093-3d41-4072-9348-8db66e9a5f3d) ![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/a0ef402c-c0eb-48ef-8fe5-8979361890d1)

Если же соседняя клетка оказалась занята, производится повторный случайный выбор направлений из возможных.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/e28c5273-ea66-4b64-b5cf-faf5b3a8d073) ![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/8d353daa-2f36-42dc-9f96-8ba2ffa5a887)

![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/556480fe-45c1-4813-af5f-36258034cbab) ![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/a6047195-58e3-4ab5-b7e9-9b5c2ac51596)

![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/4b66d62e-304c-4b20-9135-158909df54f4) ![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/c6be275f-ee12-4037-bfa3-56e0de2984ba)

![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/1990f1c2-e705-4d71-8004-653eb834e9ff) ![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/1e5d0037-6bac-4088-b46b-269e643784f8)

Построение цепочки завершается, если:  
* Длина цепочки достигла определенного для нее максимума;  
* Для текущей клетки не осталось доступных направлений, а все проверенные направления оказались неподходящими;  
* В списке свободных клеток закончились клетки.  

![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/9fd39041-ab42-4178-a201-1e6c88067452)  

Когда построение цепочки завершено, определяется ее длина. Если какая-то клетка оказывается изолированной от других (когда все клетки вокруг нее заняты; длина цепочки равна 1), то она заполняется случайной буквой из алфавита. Иначе выбирается словарь со словами из соответствующего количества букв. Из данного словаря случайным образом выбирается слово, которое последовательно по буквам переносится в ячейки полученной цепочки. Слово удаляется из словаря, а текущее слово обнуляется.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/b51dea13-84a2-48c4-8c06-8a796e8fde68)  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/a7c2e1dc-f5c5-4434-b808-6967e04ddb32)  

Таким образом алгоритм повторяется до тех пор, пока в списке свободных клеток не останется ни одной клетки.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/d66ca840-944a-4e16-a675-83d72964e34e)  

Однако в этом поле также содержатся и другие слова, которые образовались при определенном расположении относительно друг друга слов, которыми поле заполнялось.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/08b4ed7c-1f51-472e-92fa-21401dae4669)
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/88658e76-c9d5-4a74-9783-8cbe505736ee)

## 2 Предварительная настройка  
Первый этап работы – общая настройка. Для начала выполняется создание новых справочников, которые будут выступать в роли словарей.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/4e11d4ef-b342-4d8d-ab8d-bfc10b424381)  

Также необходимо создать обработку и непосредственно форму в ней для написания кода. Эта форма будет заполняться программно.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/90b7d4a8-a5ce-4b51-b62d-5a164e17131f)  
	
После этого можно запустить режим отладки и заполнить словари.  
   
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/af2cd097-500e-40e6-97c1-676d362ea427)  

## 3 Выполнение программы
Во время открытия формы обработки появляется окно для ввода размерности игрового поля.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/d71751d2-9673-420b-a9e3-3ebbbe07e384)

В результате генерируется игровое поле указанной размерности, заполненное буквами, из которых пользователь при помощи последовательных нажатий мышью может составлять слова.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/d53b3d44-e72e-4864-88c0-200a18d99bc3)

При нажатии кнопки Проверить, если данное слово есть в словаре, оно будет выведено в блоке сообщений, который отображает все найденные слова.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/23f3d578-b1dc-46a1-b478-9e8c23564f09)

Если же слово введено неверно или слово существует, но отсутствует в словаре, программа отобразит надпись о том, что слово не найдено. При определенном взаиморасположении слов могут возникнуть комбинации букв, образующие новые слова, что делает игру интереснее. Единственным недостатком этого является необходимость значительного увеличения объемов словарей.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/0eb96140-f11e-483a-a684-9cd9909e5790) 
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/992e44da-9585-4e45-85a4-9b83bc23b31a)

Если пользователь будет нажимать кнопку проверки, не введя ничего предварительно или введя только одну букву, программа, конечно же, сообщит ему, что в данной ситуации проверять ей нечего.  
  
![изображение](https://github.com/immenseR27/FillwordGame/assets/139691454/f7569a97-a1d9-47c2-98ca-0c7de6b248ef)
