# 1 Rules Overview

## PhpUnitTestToGroupRector

Add `"@group` <group>" docblock annotation to classes inheriting from given targetClass

:wrench: **configure it!**

- class: [`Basster\Rector\PhpUnit\Rector\Class_\PhpUnitTestToGroupRector`](../src/Rector/Class_/PhpUnitTestToGroupRector.php)

```php
use Basster\Rector\PhpUnit\Rector\Class_\PhpUnitTestToGroupRector;
use Basster\Rector\PhpUnit\ValueObject\PhpUnitTestToGroup;
use Rector\Config\RectorConfig;

return static function (RectorConfig $rectorConfig): void {
    $rectorConfig->ruleWithConfiguration(
        PhpUnitTestToGroupRector::class,
        [new PhpUnitTestToGroup('slow', '\Symfony\Bundle\FrameworkBundle\Test\KernelTestCase')]
    );
};
```

↓

```diff
-class SomeKernelTest extends \Symfony\Bundle\FrameworkBundle\Test\KernelTestCase
+/**
+ * @group slow
+ */
+class AddToDocBlockTest extends \Symfony\Bundle\FrameworkBundle\Test\KernelTestCase
 {
 }
```

<br>

```php
use Basster\Rector\PhpUnit\Rector\Class_\PhpUnitTestToGroupRector;
use Basster\Rector\PhpUnit\ValueObject\PhpUnitTestToGroup;
use Rector\Config\RectorConfig;

return static function (RectorConfig $rectorConfig): void {
    $rectorConfig->ruleWithConfiguration(
        PhpUnitTestToGroupRector::class,
        [new PhpUnitTestToGroup('slow', '\Symfony\Bundle\FrameworkBundle\Test\KernelTestCase')]
    );
};
```

↓

```diff
-class SomeKernelTest extends \Symfony\Bundle\FrameworkBundle\Test\WebTestCase
+/**
+ * @group slow
+ */
+class AddToDocBlockTest extends \Symfony\Bundle\FrameworkBundle\Test\WebTestCase
 {
     // \Symfony\Bundle\FrameworkBundle\Test\WebTestCase inherits from '\Symfony\Bundle\FrameworkBundle\Test\KernelTestCase'
 }
```

<br>