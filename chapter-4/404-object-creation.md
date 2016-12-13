# [译] [404] 创建对象

## Object Creation

Objects in JavaScript are sometimes created with constructor functions. For example:

    function Car(color, direction, mph) {
      this.color = color || 'pink';
      this.direction = direction || 0; // 0 = Straight ahead
      this.mph = mph || 0;

      this.gas = function gas(amount) {
        amount = amount || 10;
        this.mph %2B= amount;
        return this;
      };

      this.brake = function brake(amount) {
        amount = amount || 10;
        this.mph = ((this.mph - amount) &lt; 0)? 0
          : this.mph - amount;
        return this;
      };
    }

    var myCar = new Car();

    test('Constructor', function () {
      ok(myCar.color, 'Has a color');

      equal(myCar.gas().mph, 10,
        '.accelerate() should add 10mph.'
      );

      equal(myCar.brake(5).mph, 5,
        '.brake(5) should subtract 5mph.'
      );
    });

You can get data encapsulation by using private variables:

    function Car(color, direction, mph) {
      var isParkingBrakeOn = false;
      this.color = color || 'pink';
      this.direction = direction || 0; // 0 = Straight ahead
      this.mph = mph || 0;

      this.gas = function gas(amount) {
        amount = amount || 10;
        this.mph %2B= amount;
        return this;
      };
      this.brake = function brake(amount) {
        amount = amount || 10;
        this.mph = ((this.mph - amount) &lt; 0)? 0
          : this.mph - amount;
        return this;
      };
      this.toggleParkingBrake = function toggleParkingBrake() {
        return !!isParkingBrakeOn;
      };
    }

    var myCar = new Car();

    test('Constructor with private property.', function () {
      ok(myCar.color, 'Has a color');
      equal(myCar.gas().mph, 10,
        '.accelerate() should add 10mph.'
      );
      equal(myCar.brake(5).mph, 5,
        '.brake(5) should subtract 5mph.'
      );
      ok(myCar.toggleParkingBrake,
        '.toggleParkingBrake works.'
      );
    });

You can shave a bit of syntax using the object literal form:

    var myCar = {
      color: 'pink',
      direction: 0,
      mph: 0,

      gas: function gas(amount) {
        amount = amount || 10;
        this.mph %2B= amount;
        return this;
      },

      brake: function brake(amount) {
        amount = amount || 10;
        this.mph = ((this.mph - amount) &lt; 0)? 0
          : this.mph - amount;
        return this;
      }
    };

    test('Object literal notation.', function () {
      ok(myCar.color, 'Has a color');

      equal(myCar.gas().mph, 10,
        '.accelerate() should add 10mph.'
      );

      equal(myCar.brake(5).mph, 5,
        '.brake(5) should subtract 5mph.'
      );
    });

Notice that because the object literal form doesn't use a function, we've lost the ability to do encapsulation.
