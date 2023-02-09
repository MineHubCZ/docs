# Evaluation

To evaluate string, simply create instance of `\MineHub\Prerequisities\Evaluator` and use `eval` method. This method takes code and array of variables:

```php
$evaluator = new Evaluator();
$evaluator->eval('!(!foo || bar) && (foo && !bar)', ['foo' => true, 'bar' => false]); // returns true 
```
