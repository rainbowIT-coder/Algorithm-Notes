# 链表 (Linked List)

## 1. 核心思想
- 通过“指针”/“引用”将一组零散的内存块串联起来使用。

## 2. 基本操作与代码模板

### 节点定义
```cpp
// 单链表节点
struct ListNode {
    int val;
    ListNode *next;
    ListNode(int x) : val(x), next(nullptr) {}
};
```

### 遍历链表
```cpp
void printList(ListNode* head) {
    ListNode* current = head;
    while (current != nullptr) {
        cout << current->val << " ";
        current = current->next;
    }
}
```

## 3. 经典技巧与应用
### 快慢指针
- **应用**：判断环、找中点、找倒数第K个节点。
- **例题**：
    - [LC 141. 环形链表](https://leetcode.cn/problems/linked-list-cycle/)
    - [LC 876. 链表的中间结点](https://leetcode.cn/problems/middle-of-the-linked-list/)

## 4. 易错点
- **丢失头节点**：`ListNode* temp = head;` 用临时变量去遍历。
- **循环条件**：`while (current != nullptr)` 还是 `while (current->next != nullptr)` 要分清。
- **空指针解引用**：在访问 `current->val` 或 `current->next` 前要确保 `current != nullptr`。

## 5. 相关练习
| 题目 | 难度 | 关键点 |
| :--- | :--- | :--- |
| [LC 206. 反转链表](https://leetcode.cn/problems/reverse-linked-list/) | 简单 | 双指针/递归 |
| [LC 203. 移除链表元素](https://leetcode.cn/problems/remove-linked-list-elements/) | 简单 | 虚拟头节点 |
| [LC 19. 删除链表的倒数第 N 个结点](https://leetcode.cn/problems/remove-nth-node-from-end-of-list/) | 中等 | 快慢指针 |