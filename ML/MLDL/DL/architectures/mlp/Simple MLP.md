*MLP* (Multilayer Perceptron) - многослойный перцептрон, первая архитектура глубокой сети прямого распространения без обратных связей, предложенная Розенблатом в *1958*, в основе архитектуры лежит идея об [[Искусственный нейрон|искусственном нейроне]].

Состоит из:
1. Входной слой
2. Один или несколько скрытых слоев
3. Выходной слой

Обучается с помощью алгоритма [[Backprop|обратного распространения ошибки]].

Цель сети прямого распространения аппроксимировать некоторую функцию $f^*$, например, в случае задачи классификации функцию $y=f^*(x)$ отобразить вход $x$ в категорию $y$.

Сеть прямого распространения определяет отображение $y=f(x, \theta)$ и путем обучения находит значения параметров $\theta$. 

Размерность скрытых слоев определяет *ширину* модели. Слои вырабатывают векторные значения, элементы этого вектора можно интерпретировать как *нейрон*. 
## Необходимость глубокой сети

Глубокая нейронная сеть преодолевает ограничения линейных моделей, например линейной регрессии, чья емкость ограничена линейными функциями.

До появления глубоких сетей ограничения линейности преодолевали путем применения нелинейных преобразований $\phi$ к $x$, получая новые представления $x$. Далее линейная модель применялась не к самому $x$ а к новому представлению $\phi(x)$.

У такого подхода есть недостаток - каждый раз необходимо выбирать функцию $\phi$ в зависимости от решаемой задачи, чтобы качество модели улучшалось, а не ухудшалось. Это необходимо делать вручную или перебором. 

Для решения этого недостатка глубокая сеть предоставляет решение - использовать параметрическую функцию $\phi(x, \theta)$ и находить параметры $\theta$ в процессе обучения модели, $\phi$ при таком подходе определяет скрытый слой сети. В качестве $\phi$ выступает композиция аффинного преобразования и нелинейной функции активации.
**Например**:
линейная регрессия вида $y = f(x, w)$ преобразуется к виду $y=\phi(x, \theta)^Tw$ (1 скрытый слой)
## Скрытые слои


  

