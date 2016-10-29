
template <typename T>
void List<T>::merge(List<T>& listA,List<T>& listB)
{
   bool done=false;
   Node *tempHead,*current,*currentA,*currentB;
   tempHead=NULL;
   currentA=listA.head;
   currentB=listB.head;

   while(!done)
   {
      if (currentA == NULL && currentB == NULL) {
         done=true;

      //edge append B
      } else if (currentA == NULL) {
         
    	  if (tempHead == NULL)
            tempHead = currentB;
          else
            current->next = currentB;
            done=true;
      //edge append A
      } else if (currentB == NULL) {
         if (tempHead == NULL)
            tempHead = currentA;
         else
            current->next = currentA;
         done=true;
      } else if (*currentA->data < *currentB->data) {

            if (tempHead == NULL) {
               tempHead = currentA;
               current = currentA;
            } else {
               current->next = currentA;
               current = currentA;
            }
            currentA=currentA->next;   //walk A
      } else {
            if (tempHead == NULL) {
               tempHead = currentB;
               current = currentB;
            } else {
               current->next = currentB;
               current = currentB;
            }
            currentB=currentB->next;   //walk B
      }

   }//end while

   //lists are merged remove pointer to lists

   if (this != &listA)
   {
      listA.head = NULL;
   }

   if (this != &listB)
   {
      listB.head = NULL;
   }
   this->head = tempHead;
}
