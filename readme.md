** Manual **

** simpleheat reference: https://github.com/mourner/simpleheat **

** Generate data points with normal distribution **

    var Kconst = 1 / ( Math.PI * Math.sqrt(2) );
    var dataset = [];
    
    for(var index = 0; index < 500; index++) {
    
        var point = [];
        point.push( Math.floor( Math.random() * 320) + 1 );
        point.push( Math.floor( Math.random() * 480) + 1 );
        point.push( (Kconst * Math.exp( Math.pow( Math.random(), 2 ) * (-0.5) )));
        dataset.push(point);
    }

** constructor -> create a simpleheat object given an id or canvas reference **

    var heat = simpleheat("paper"),
      minOpacity = 0.05,
      max = 1,
      point = [ 150, 240, 2 ],
      r = 25,
      r2 = 15,
      grad = { 0.4: 'blue', 0.65: 'lime', 1: 'red' };

** bind data -> set data of [[x, y, value], ...] format **

    heat.data(dataset);

** set max data value (1 by default) **

    heat.max(max);

** add a data point **

    heat.add(point);

** clear data **

    heat.clear();

** set point radius and blur radius (25 and 15 by default) **

    heat.radius(r, r2);

** set gradient colors as {<stop>: '<color>'}, e.g. {0.4: 'blue', 0.65: 'lime', 1: 'red'} **

    heat.gradient(grad);
    heat.draw(minOpacity);