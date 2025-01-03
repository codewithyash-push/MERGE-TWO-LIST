class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def mergeTwoLists(self, list1, list2):
        # Create a dummy node to simplify the merging process
        dummy = ListNode()
        current = dummy  # This will point to the last node in the merged list

        while list1 and list2:
            if list1.val < list2.val:
                current.next = list1  # Attach list1 node to the merged list
                list1 = list1.next  # Move list1 pointer to the next node
            else:
                current.next = list2  # Attach list2 node to the merged list
                list2 = list2.next  # Move list2 pointer to the next node
            current = current.next  # Move the current pointer to the last node in merged list

        # If there are remaining nodes in either list, attach them
        if list1:
            current.next = list1
        if list2:
            current.next = list2

        # Return the merged list, starting from dummy.next
        return dummy.next

# Helper function to create a linked list from a list of values
def create_linked_list(values):
    dummy = ListNode()
    current = dummy
    for value in values:
        current.next = ListNode(value)
        current = current.next
    return dummy.next

# Helper function to print a linked list (compatible with Python 2)
def print_linked_list(head):
    current = head
    while current:
        # Print the current value, check if there is a next node to add "->"
        if current.next:
            print current.val, "->",  # Python 2 print statement
        else:
            print current.val, "-> None"  # Last value followed by "-> None"
        current = current.next

# Example usage
list1 = create_linked_list([1, 2, 4])
list2 = create_linked_list([1, 3, 4])

# Create Solution object and call mergeTwoLists method
solution = Solution()
merged_head = solution.mergeTwoLists(list1, list2)

# Print the merged linked list
print_linked_list(merged_head)
