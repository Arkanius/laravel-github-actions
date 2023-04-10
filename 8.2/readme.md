# Laravel Test Runner - PHP 8.2

Docker Container with PHP 8.2 and extensions to be compatible with most Laravel applications. Also installed on this container we have Composer 2 and NodeJS/NPM/Yarn.

## Building and pushing the image

**Build**:

```
docker build --pull -t vtrgomes/github-actions-laravel:8.2 .
```

**Tag**:

```
docker tag vtrgomes/github-actions-laravel:latest vtrgomes/github-actions-laravel:8.2
```

**Push**:

```
docker push vtrgomes/github-actions-laravel:8.2
```

## Credits

- [Luis Dalmolin](https://github.com/luisdalmolin)

## Sponsorship

Development of this package is sponsored by Kirschbaum Development Group, a developer driven company focused on problem solving, team building, and community. Learn more [about us](https://kirschbaumdevelopment.com) or [join us](https://careers.kirschbaumdevelopment.com)!
