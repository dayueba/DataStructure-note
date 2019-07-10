 顺序表

```
// 顺序表
typedef struct {
    int data[maxSize];
    int length;
}Sqlist;

// 考试中用的最多的顺序表定义
int A[maxSize];
int n;

// 单链表
typedef struct LNode{
    int data;
    struct LNode *next;
}LNode;

// 双链表
typedef struct DLNode{
    int data;
    struct DLNode *prior;
    struct DLNode *next;
}DLNode;

// 申请新的空间
LNode *node = (LNode *)malloc(sizeof(LNode));

// 查找第一个比x大的元素
int findElem(Sqlist L, int x){
    int i;
    for (i = 0; i < L.length; ++i) {
        if( x < L.data[i]){
            return i;
        }
    }
    return i;
}

void insertELem(Sqlist &L, int x){
    int i = findElem(L, x), j;
    for (j = L.length; j > i; j--) {
        L.data[j] = L.data[j-1];
    }
    L.data[i] = x;
    L.length ++;
}

// 查找第一个值等于e的元素
int findE(Sqlist L, int e){
    for (int i = 0; i < L.length; ++i) {
        if( L.data[i] == e )
            return i;
    }
    return -1;
}

// 插入元素
int insertElem(Sqlist &L, int e, int p){
    if( p < 0 || p >L.length || L.length == maxSize )
        return 0;
    for (int i = L.length; i > p; i--) {
        L.data[i] = L.data[i-1];
    }
    L.data[p] = e;
    L.length ++;
    return 1;
}

// 删除下标为p【0，len-1】的元素
int deleteElem(Sqlist L, int p, int &e){
    if( p < 0 || p >=L.length )
        return 0;
    e = L.data[p];
    (L.length) --;
    for (int i = p; i < L.length; ++i) {
        L.data[i] = L.data[i+1];
    }
    return 1;
}

// 初始化顺序表
void initList(Sqlist &L){
    L.length = 0;
}

// 返回指定位置的元素 [0, len-1]
int getElem(Sqlist L, int p, int &e){
    if( p < 0 || p > L.length-1 )
        return 0;
    e = L.data[p];
    return 1;
}
```



