# Docker Container for running Laravel tests

[![Docker Badge](https://img.shields.io/docker/pulls/vtrgomes/github-actions-laravel)](https://img.shields.io/docker/pulls/vtrgomes/github-actions-laravel/)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://hub.docker.com/repository/docker/vtrgomes/github-actions-laravel)


| PHP version | Link | Container Tag |
| ----------- | ---- |  ------------- |
| 8.2 | [🔗](https://github.com/Arkanius/laravel-test-runner-container/blob/master/8.2/Dockerfile) | vtrgomes/github-actions-laravel:8.2 |
| 7.4 | [🔗](https://github.com/Arkanius/laravel-test-runner-container/blob/master/7.4/Dockerfile) | vtrgomes/github-actions-laravel:7.4 |
| 7.3 | [🔗](https://github.com/Arkanius/laravel-test-runner-container/blob/master/7.3) | vtrgomes/github-actions-laravel:7.3 |
| 7.2 | [🔗](https://github.com/Arkanius/laravel-test-runner-container/blob/master/master/7.2) | vtrgomes/github-actions-laravel:7.2 |


## Credits

- [Luis Dalmolin](https://github.com/luisdalmolin)
- [kirschbaum](https://github.com/kirschbaum-development/laravel-test-runner-container)


## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.

## Example

Checkout this example to see how to run a simple laravel pipeline. Create a file at *.github/workflows* with the follow contents:

**.github/workflows/tests.yml**

```yaml
name: Unit Tests
on: [push, pull_request, release]
jobs:
  PhpUnit:
    runs-on: ubuntu-latest
    container:
      image: vtrgomes/github-actions-laravel:latest

    services:
      mysql:
        image: mysql:5.7
        env:
          MYSQL_ROOT_PASSWORD: root
          MYSQL_DATABASE: secret
        ports:
          - 33306:3306
        options: --health-cmd="mysqladmin ping" --health-interval=10s --health-timeout=5s --health-retries=3
      
      redis:
        image: redis:latest
        ports:
          - 6379:6379
  
    steps:
    - uses: actions/checkout@v2
      with:
        fetch-depth: 1

    - name: Install composer dependencies
      run: |
        composer install --no-scripts

    - name: Prepare Laravel Application
      run: |
        cp .env.ci .env
        php artisan key:generate

    - name: Run Testsuite
      run: vendor/bin/phpunit
```

now, just push into your repository and se the **actions** running!
