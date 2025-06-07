Apunts de  midudev per fer scrapy:

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
    const products = await page.$$eval('.s-card-container', (results) => results.map((el) => {
        
    }))