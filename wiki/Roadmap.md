## Objectius:

- Maquetar un input per introduïr-hi l'enllaç al vídeo de tv3, o el codi.
- Aïllar el codi.
- Consultar `https://dinamics.ccma.cat/pvideo/media.jsp?media=video&version=0s&idint=6343012`
- Analitzar tota la informació disponible a dinamics.ccma.cat

### Apunts de  midudev per fer scrapy:

- 1 Nou projecte de Node: `npm init -y`
- 2 Instalar dependencia Playwright: `npm install playwright`
- 3 Nou arxiu `index.mjs`
- 4 Importar chromium de playwright: 
    ```js
    import { chromium } from 'playwright'
    ```
- 5 Obrir el navegador sense obrir cap finestra:
    ```js
    const browser = await chromium.launch({ headless: true })
    ```
- 6 Obrim una pàgina: 
    ```js
    const page = await browser.newPage()
    
    await page.goto('http://www.domini.com/...')
    ```
- 7 Capturar "productes":
    ```js
    const products = await page.$$eval('.s-card-container', (results) => (results.map((el) => {

        const title = el.querySelector('h2')?.innerText

        if (!title) return null

        const image = el.querySelector('img').getAttribute('src')

        const price = el.querySelector('.a-price .a-offscreen')?.innerText

        const link = el.querySelector('.a-link-normal').getAttribute('href')

        return { title, image, price, link }

        })
    ))

    consolle.log(products)
    await browser.close()
    ```

### Notes:

    El que creia que seria un projete d'scrapy sembla que resultarà mes senzill: 
    1 Trobar l'id del vídeo desitjat
    2 Investigar la informació disponible a `https://dinamics.ccma.cat/pvideo/media.jsp?media=video&version=0s&idint=6343012`
    3 Mostrar la informació del vídeo: qualitats, idiomes, subtítols

    4 Mes endavant afegirem un input per personalitzar el nom d'arxiu i descarregar-lo.
    5 Potser es podrà oferir la opció de combinar video i subtítols en un mateix arxiu.s

