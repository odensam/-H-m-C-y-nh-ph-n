# -H-m-C-y-nh-ph-n#include <conio.h>
#include <stdio.h>
#include <alloc.h>
#include <malloc.h>
//Khai bao cay nhi phan
typedef char TData;
typedef struct TNode{
    TData Data;
    TNode* left;
    TNode* right;
};
typedef TNode* TTree;
//Tao cay rong
void MakeNull_Tree(TTree *T) {
    (*T) = NULL;
}
//Kiem tra cay rong
bool EmptyTree(TTree T) { // bool _ not void
    return T == NULL;
}
//Xac dinh con trai
TTree LeftChild(TTree T){
      if (T!=NULL) return T->left;
      else return NULL;}
//Xac dinh con phai
TTree RightChild(TTree T) {
    if (T!=NULL) return T->right;
    else return NULL;
}
//Kiem tra nut la
bool IsLeaf(TTree T){
    return ((T!=NULL)&&(T->left==NULL)&&(T->right==NULL));
}
//Tao cay tu 2 cay con cho truoc
TTree Create2(TData v, TTree left, TTree right){
    TTree N;
    N=(TNode*)malloc(sizeof(TNode));
    N->Data=v;
    N->left=left;
    N->right=right;
        return N;
}
//Duyet tien tu
void NLR(TTree T) {
    if(!EmptyTree(T)) {
        printf(“%c, “, T->Data);
        NLR(LeftChild(T));
        NLR(RightChild(T));
    }
}
//Duyet trung tu
void LNR(TTree T) {
    if (!EmptyTree(T)) {
        LNR(LeftChild(T));
        printf(“%c, “,T->Data);
        LNR(RightChild(T));
    }
}
//Duyet hau tu
void LRN(TTree T){
     if (!EmptyTree(T)){
        LRN(LeftChild(T));
        LRN(RightChild(T));
        printf(“%c, “, T->Data);}
}
