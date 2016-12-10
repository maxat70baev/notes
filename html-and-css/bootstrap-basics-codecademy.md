# [Using Bootstrap](http://getbootstrap.com/getting-started/)

## Grid system
![](https://s3.amazonaws.com/codecademy-content/courses/make-a-website/img/grid.svg)
* Bootstrap's grid columns are represented by 12 vertical bars. The boxes represent HTML elements.
* The words `container`, `jumbotron`, `col-sm-6` and `col-sm-3` refer to Bootstrap classes. 
* The element with class `jumbotron` spans the entire width of the webpage, beyond the borders of the grid. 
* Elements inside the second `container`, such as `col-sm-6` and `col-sm-3` are contained within the grid columns. 
* Elements labeled `col-sm-3` take up three grid columns; elements labeled `col-sm-6` take up six grid columns.

## Example of header/navigation bar
```
<header class="container">
	<div class="row">
    <h1 class="col-sm-4">Skillfair</h1>
    <nav class="col-sm-8 text-right">
      <p>newest</p>
      <p>catalogue</p>
      <p>contact</p>
    </nav>
  </div>
</header>
```

## Example of jumbotron
```
<section class="jumbotron">
	<div class="container">
  	<div class="row text-center">
      <h2>Homemade Goods</h2>
      <h3>This Year's Best</h3>
      <a class="btn btn-primary" href="#" role="button">See all</a>
    </div>
  </div>
</section>
```

## Example of supporting content
```
<section class="container">
	<div class="row">
		<figure class="col-sm-6">
      <p>kitchen</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/kitchen.jpg" />
    </figure>
 		<figure class="col-sm-6">
      <p>woodwork</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/woodwork.jpg" />
    </figure>
  </div>
  <div class="row">
		<figure class="col-sm-6">
      <p>gifts</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/gifts.jpg" />
    </figure>
    <figure class="col-sm-6">
      <p>antiques</p>
      <img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/antique.jpg" />
    </figure>
  </div>
</section>
```

## Example of footer
```
<footer class="container">
	<div class="row">
    <p class="col-sm-4">&copy; 2016 Skillfair</p>
    <ul class="col-sm-8">
      <li class="col-sm-1">
      	<img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/twitter.svg" />
      </li>
			<li class="col-sm-1">
      	<img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/facebook.svg" />
      </li>
			<li class="col-sm-1">
      	<img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/instagram.svg" />
      </li>
      <li class="col-sm-1">
				<img src="https://s3.amazonaws.com/codecademy-content/projects/make-a-website/lesson-4/medium.svg" />
      </li>
    </ul>
  </div>
</footer>
```