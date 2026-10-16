### Лабораторна робота №2

**Варіант 3**

**Хід роботи**

**Завдання 1.** Для виконання завдання розбиваємо речення на логічні групи взаємопов'язаних фактів та визначаємо кілька узагальнюючих шаблонів для родинних зв'язків та характеристик особи. Далі формуємо для них єдиний список `deffacts`.
```
(deftemplate parent-relation
   (slot parent-type)
   (slot parent-name)
   (slot child-name)
)

(deftemplate parents-of
   (slot child)
   (multislot parents)
)

(deftemplate person-profile
   (slot name)
   (slot gender)
   (slot role) 
)

(deffacts family-knowledge-base
   (parent-relation (parent-type father) (parent-name Tom) (child-name John))
   (parent-relation (parent-type mother) (parent-name Susan) (child-name John))

   (parents-of (child John) (parents Tom Susan))
   
   (person-profile (name Tom) (gender male) (role father))
   (person-profile (name Susan) (gender female) (role mother))
   (person-profile (name John) (gender male) (role son))
)
```

**Завдання 2.** Створюємо єдину структуру за допомогою `deftemplate flight` для всіх рейсів із двома слотами: `from` (звідки) та `to` (куди). Далі задаємо набір фактів `airline-network` використовуючи `deffacts`, що повністю відповідають напрямкам стрілок між містами на схемі.
```
(deftemplate flight
   (slot from)
   (slot to)  
)

(deffacts airline-network
   (flight (from "Сан-Франциско") (to "Чикаго"))
   (flight (from "Сан-Франциско") (to "Лос-Анджелес"))
   (flight (from "Лос-Анджелес") (to "Хьюстон"))
   (flight (from "Хьюстон") (to "Сан-Франциско"))
   (flight (from "Чикаго") (to "Индианаполис"))
   (flight (from "Индианаполис") (to "Хьюстон"))
   (flight (from "Хьюстон") (to "Нью-Йорк"))
   (flight (from "Нью-Йорк") (to "Чикаго"))
)
```
