# ๐ก Semantic Tag?
- ์ปดํจํฐ๊ฐ ์ ๋ณด๋ฅผ ์ฝ๊ณ , ์ดํด, ๊ฐ๊ณตํ์ฌ ์๋ก์ด ์ ๋ณด๋ฅผ ๋ง๋ค์ด ๋ผ ์ ์๋๋ก ๋ง๋  ์ง๋ฅํ ์น

### Layout Tag
#### `<header>`
- ์ผ๋ฐ์ ์ผ๋ก ์น ํ์ด์ง์ ๊ฐ์ฅ ์๋ถ๋ถ์ ์์นํจ
- ์น ํ์ด์ง์ ์ ๋ชฉ์ด๋, ์๋จ๋ฐ ํน์ ๊ฒ์์ฐฝ ๋ฑ์ด ํฌํจ๋จ.
#### `<nav>`
- navigation์ ์ฝ์๋ก, ์ฌ์ดํธ์ ํญ์ ํฌํจํ๊ณ  ์์
- `<nav>` tag์์ list tag๋ค์ ๋ฃ์ด ์ฌ์ฉ
#### `<main>`
- ์ฌ์ดํธ์ ๋ฉ์ธ ์ฝํ์ธ ๋ฅผ ํฌํจ
#### `<section>`
- ์น ํ์ด์ง์ ์น์์ ๋ํ๋ด๋ Tag
- ํ์ด์ง๋ฅผ Part๋ณ๋ก ๋๋๊ธฐ ์ํด์๋ ์ฌ์ฉ๋จ
#### `<aside>`
- ๋ณธ๋ฌธ์ด ๋๋๊ณ  ์ถ๊ฐ ๋ด์ฉ์ ํฌํจํ๋ Tag
- ๊ด๊ณ  ๋ฑ์ด ๋ค์ด๊ฐ๊ธฐ๋ ํจ
#### `<footer>`
- ๋ณดํต ํ์ด์ง์ ๊ฐ์ฅ ํ๋จ๋ถ์ ์์น
- CopyRight ๋ฐ ๋ผ์ด์ผ์ค ๋ฑ์ด ํฌํจ๋จ

### ๐ ์์
>```
> <!DOCTYPE html>
>   <html lang="ko">
>   <head>
>     <meta charset="utf-8">
>     <title>FastCampus</title> // ํ์ด์ง ์ ๋ชฉ
>   </head>
>   <body>
>  	 <header>
>  	   <h1>Megabyte School</h1> // ์ฌ์ดํธ ์ ๋ชฉ
>      <h2>HTML</h2> // ์ฌ์ดํธ ๋ถ์ ๋ชฉ
>  	   <nav>
>     	 <ul>
>   	   <li>HTML ์ด๋?</li>     // ๋ฉ๋ด1
>   	   <li>HTML Tags</li>     // ๋ฉ๋ด2
>		   <li>Semantic Tags</li> // ๋ฉ๋ด3
>         </ul>
>	   </nav>
>	 </header>
>	   <main>
>	     <p>HTML ์ค๋ช</p> // ๋ณธ๋ฌธ ๋ด์ฉ
>	   </main>
>	   <aside>
>	     ๊ด๊ณ ..๋ฑ๋ฑ
>	   </aside>
>	   <footer>
>	  	 <p>LICENSE</p>
>	   </footer>
>	</body>
> </html>
>```
<!DOCTYPE html>
<html lang="ko">
	<head>
		<meta charset="utf-8">
	</head>
	<body>
		<header>
			<h1>Megabyte School</h1>
			<h2>HTML</h2>
			<nav>
				<ul>
					<li>HTML ์ด๋?</li>
					<li>HTML Tags</li>
					<li>Semantic Tags</li>
				</ul>
			</nav>
		</header>
		<main>
			<p>HTML ์ค๋ช</p>
		</main>
		<aside>
			๊ด๊ณ ..๋ฑ๋ฑ
		</aside>
		<footer>
			<p>LICENSE</p>
		</footer>
	</body>
</html>
