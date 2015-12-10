# definition-interop container's test suite

Modules (aka packages or bundles) are widespread in modern frameworks. Unfortunately each framework has its own convention and tools for writing them. The goal of *container-interop* and more specifically *definition-interop* is to help developers write modules that can work in any framework.

*definition-interop* contains interfaces helping developers describe container definitions (objects that can be cast to a container entry).

This package contains a set of test suites that can be used to ensure that a container/compiler is indeed compatible with *definition-interop*.

## How does it work?

This package contains a number of definition instances, and the associated PHPUnit tests that should match those instances.

Container / compilers compatible with *container-interop* should be able to pass any of those tests.

## Usage

This package contains a `AbstractDefinitionCompatibilityTest` class. This is an abstract PHPUnit test class.
In your package, you should extend this class and implement 2 abstract methods:

- `compileDefinitions` method: This method should return a container-interop compatible container.
- `shouldRunDefensiveProgrammingTests` method: This method should return `true` or `false`. Return true if you want to test your container against defensive programming best practices. If you enable this, tests will provide invalid data to your container and it is expected that your container will throw an exception. Defensive programming tests are out-of-scope of *definition-interop* so they are not compulsory, only recommended.
