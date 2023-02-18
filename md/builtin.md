# builtin関数
---
- echo  
```
#include <libc.h>

int	is_opn(char *s);

int	ft_strncmp(const char *s1, const char *s2, size_t n)
{
	size_t	i;

	i = 0;
	while (i < n)
	{
		if (s1[i] != s2[i] || !s1[i] || !s2[i])
			return ((unsigned char)s1[i] - (unsigned char)s2[i]);
		i++;
	}
	return (0);
}

int	main(int argc, char *argv[])
{
	size_t	i;
	int		not_work;

	if (argc == 1)
		return (printf("\n") * 0);
	i = 1;
	not_work = 0;
	while (argv[i] && is_opn(argv[i]))
	{
		not_work = 1;
		i++;
	}
	while ((int)i < argc)
	{
		printf("%s", argv[i]);
		i++;
		if ((int)i < argc)
			printf(" ");
	}
	if (!not_work)
		printf("\n");
	return (0);
}

int	is_opn(char *s)
{
	if (ft_strncmp(s, "-n", 2))
		return (0);
	s++;
	while (*s == 'n')
		s++;
	if (!(*s))
		return (1);
	return (0);
}
```