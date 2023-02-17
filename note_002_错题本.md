排错
1.指针
原题：
void getmemory(char *p)
{
    p = (char *)malloc(100);
    memset(p, 0, 100);
    memcpy(p, "123", strlen("123"));
}
 
int main(void)
{        
    char *str = NULL;
 
    getmemory(str);
    printf("%s\n", str);
 
    free(str);
 
    return 0;
}
输出null，且崩溃(free空指针)
 
正确：
void getmemory(char **p)
{
    *p = (char *)malloc(100);
    memset(*p, 0, 100);
    memcpy(*p, "123", strlen("123"));
}
 
int main(void)
{        
    char *str = NULL;
 
    getmemory(&str);
    printf("%s\n", str);
 
    free(str);
 
    return 0;
}