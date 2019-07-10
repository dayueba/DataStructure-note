### 单链表

1. 带头节点
2. 不带头节点

```
// 合并两个升序的单链表 升序
// 尾插法
void merge(LNode *A, LNode *B, LNode *&C){
    LNode *p = A->next;
    LNode *q = B->next;
    LNode *r;
    C=A;
    C->next = NULL;
    free(B);
    r = C;

    while (p != NULL && q != NULL){
        if( p->data <= q->data ){
            r->next = p;
            p = p->next;
            r = r->next;
        } else {
            r->next = q;
            q = q->next;
            r = r->next;
        }
    }
//    r->next = NULL;

    if( p!=NULL )r->next=p;
    if( q!=NULL )r->next=q;
}


// 尾插法建立链表C
// 每次都把新节点插入尾部
void createlistR(LNode *&C, int a[], int n){
    LNode *s, *r;
    int i;
    C = (LNode *)malloc(sizeof(LNode));
    C->next = NULL;
    r = C;

    for (i = 0; i < n; ++i) {
        s = (LNode *)malloc(sizeof(LNode));
        s->data = a[i];
        r->next = s;
        r = r->next;
    }

    r->next = NULL;
}

// 头插法建立链表C
// 每次都把节点插入头部
void createlistF(LNode *&C, int a[], int n){
    LNode *s;
    int i;
    C = (LNode *)malloc(sizeof(LNode));
    C->next = NULL;

    for (i = 0; i < n; ++i) {
        s = (LNode *)malloc(sizeof(LNode));
        s->data = a[i];
        // 关键步骤
        s->next = C->next;
        C->next = s;
    }
}

// 合并两条升序链表 倒序排列
// 使用头插法
// todo


/*
 * p节点之后插入s节点
 * s->next = p->next;
 * p->next = s;
 *
 *
 * 删除节点s的下一个节点
 * p = s->next;
 * s->next=q->next;
 * free(p);
 *
 *
 * */

// 查找链表c中是否存在值为x的节点 存在则删除
int findAndDelete(LNode *C, int x){
    LNode *p, *q;
    p = C;
    while (p->next != NULL){

        if( p->next->data == x)
            break;
        p = p->next;
    }
    
    if( p->next == NULL){
        return 0;
    }
    
    q = p->next;
    p->next = q->next;
    free(q);
    return 1;
}
```

### 双链表

### 循环单链表

最后一个节点的指针指向第一个节点（如果有头节点 则指向头节点）

* 带头节点 head == head-&gt;next时为空
* 不带头节点 head == NULL 为空

### 循环双链表

最后一个节点指向第一个节点 第一个节点指向最后一个节点

* 带头节点 head-&gt;next head-&gt;prior 任意一个等于head 为空
* 不带头节点 head == NULL 为空

### 静态链表

记录后继节点在数组中位置

