<h1 align="center">  
  <img src="https://github.com/4Sin/ya_music_covers/blob/main/2023-10-20_09.47.37.jpg" width="800"/> 
  Обнаружение каверов музыкальных треков
</h1>  
  
 
### 🛠️ Стек технологий:
<div id="tools", align="center">
  <img src="https://github.com/devicons/devicon/blob/master/icons/pandas/pandas-original-wordmark.svg" title="Pandas" alt="Pandas" width="40" height="40"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/numpy/numpy-original-wordmark.svg" title="NumPy" alt="NumPy" height="40"/>&nbsp;
  <img src="https://seaborn.pydata.org/_images/logo-tall-lightbg.svg" title="Seaborn" alt="Seaborn" width="40" height="40"/>&nbsp;
  <img src="https://aip.media/wp-content/uploads/2019/11/Google_BERT_v1.jpg" title="BRT" alt="BERT" height="40"/>&nbsp;
  <img src="https://quintagroup.com/cms/python/images/scikit-learn-logo.png" title="Scikit learn" alt="Scikit learn" height="40"/>&nbsp;
  <img src="https://upload.wikimedia.org/wikipedia/commons/d/d9/LightGBM_logo_black_text.svg" title="LightGBM" alt="LightGBM" height="40"/>&nbsp;
  <img src="https://pypi-camo.global.ssl.fastly.net/d60a70af6de88eae24a88d3c21d81adbfb7d3b6c/68747470733a2f2f68756767696e67666163652e636f2f64617461736574732f68756767696e67666163652f646f63756d656e746174696f6e2d696d616765732f7261772f6d61696e2f7472616e73666f726d6572732d6c6f676f2d6c696768742e737667" title="Transformers" alt="Transformers" height="40"/>&nbsp;
</div>

## Содержание
- 🔌 [Описание данных](#описание-данных)
- 🐥 [EDA](#eda)
- 🔨 [Предобработка данных](#предобработка-данных)
- 😻 [Обучение моделей](#обучение-моделей)
- 📄 [Проверка на тестовых данных](#проверка-на-тестовых-данных)
- ❗️ [Вывод](#вывод)

## Описание данных

Обнаружение треков каверов - важная продуктовая задача, которая может значительно улучшить качество рекомендаций музыкального сервиса и повысить счастье наших пользователей.

## covers

- `track_id` - уникальный идентификатор трека;
- `track_remake_type` - метка, присвоенная редакторами. Может принимать значения ORIGINAL и COVER;
- `original_track_id` - уникальный идентификатор исходного трека.

## lyrics

- `track_id` - уникальный идентификатор трека; 
- `lyricId` - уникальный идентификатор текста; 
- `text` - текст трека. 

## meta

- `track_id` - уникальный идентификатор трека; 
- `dttm` - первая дата появления информации о треке; 
- `title` - название трека; 
- `language` - язык исполнения;
- `isrc` - международный уникальный идентификатор трека; 
- `genres` - жанры; 
- `duration` - длительность трека.

## EDA

- Обнаружены пропуски значений в столбцах;
- В данных дубликаты удалены. 

## Предобработка-данных

- Удалены пропуски в столбце `isrc`.
- Добавлен новый признак 'isrc_year' с помощью столбца `isrc`.
- Столбец `title` очищен от знаков препинаний и символов.
- Применен BERT для токенизации столбца `title`.

## Обучение-модели

- Обучены 3 ML-модели: LR, LightGBM, CatBoost, лучшую метрику показала LightGBM.
- Найдены лучшие гиперпараметры для модели через GreedSearchCV.;
- Лучшие гиперпараметры модели:
  ``` python
    { 'learning_rate': 0.01, 'max_depth': 25, 'num_iterations': 700, 'num_leaves': 31 };
  ```
## Проверка-на-тестовых-данных

- AUC равен 0.887, это означает, что существует 88,7% вероятность того, что модель сможет отличить положительный класс от отрицательного класса. 

## Вывод
<br> ⚡️ Было проведено исследование, для<b> прогнозирования обнаружения каверов музыкальных треков.</b> 
              
<br><b> Входные данные - исторические данные от Яндекс музыка. </b>

<br> ⚡️ Проведена предобработка данных:

- Удалены неинформативные признаки; 
- Удалены пропуски в столбце `isrc`; 
- Добавлен новый признак `year`; 
- Применен BERT для токенизации столбца `title`. 

        
<br> ⚡️ Обучена модель LightGBM.
        
<br> ⚡️ Найдены лучшие гиперпараметры для модели с помощью GridSearchCV.
        
<br> ⚡️ Показано качество исследованной модели с помощью метрики AUC на тестовой выборке.
