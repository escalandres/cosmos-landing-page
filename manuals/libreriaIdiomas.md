# Manual para implementar una librería de idiomas en React.JS
### Dependencias necesarias:
````
npm install i18next react-i18next
# o
npm install react-intl
````

### Organizacion de los archivos
````
src/
└── translations/
    ├── en.json
    ├── es.json
    └── fr.json
````

## Configuración de biblioteca de traducción
````
import i18n from 'i18next';
import { initReactI18next } from 'react-i18next';

i18n
  .use(initReactI18next) // Para React
  .init({
    resources: {
      en: {
        translation: require('./translations/en.json'),
      },
      es: {
        translation: require('./translations/es.json'),
      },
      fr: {
        translation: require('./translations/fr.json'),
      },
    },
    lng: 'en', // Idioma predeterminado
    fallbackLng: 'en', // Idioma de respaldo
    interpolation: {
      escapeValue: false,
    },
  });

export default i18n;
````

## Utilización de la librería de idiomas
````
import React from 'react';
import { useTranslation } from 'react-i18next';

function MyComponent() {
  const { t } = useTranslation();

  return (
    <div>
      <h1>{t('greeting')}</h1>
      <p>{t('description')}</p>
    </div>
  );
}

export default MyComponent;
````

## Componente para el selector de idioma
````
// LanguageSelector.js
import React from 'react';

const LanguageSelector = ({ languages, currentLanguage, onLanguageChange }) => {
  return (
    <div className="language-selector">
      <label htmlFor="language-select">Select Language:</label>
      <select
        id="language-select"
        value={currentLanguage}
        onChange={(e) => onLanguageChange(e.target.value)}
      >
        {languages.map((language) => (
          <option key={language} value={language}>
            {language}
          </option>
        ))}
      </select>
    </div>
  );
};

export default LanguageSelector;
````

## Contenido de los archivos .json
### ingles: en.json
````
{
  "greeting": "Hello, World!",
  "description": "This is a sample description.",
  "buttonLabel": "Click Me"
}

````

### español: es.json
````
{
  "greeting": "¡Hola, Mundo!",
  "description": "Esta es una descripción de ejemplo.",
  "buttonLabel": "Haz clic"
}
````

