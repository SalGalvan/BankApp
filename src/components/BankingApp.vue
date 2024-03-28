<script>
import { ref } from 'vue';
 
export default {
  setup() {
    const accounts = ref([
      { accountNumber: '1', accountHolder: 'Sal G.', balance: 1000 },
      { accountNumber: '2', accountHolder: 'Tim R.', balance: 500 }
    ]);
 
    const transferAmount = ref(0);
    const recipientAccountNumber = ref('');
    const transferMessage = ref('');
 
    const transfer = () => {
      const senderAccount = accounts.value.find(account => account.accountHolder === 'Sal G.');
      const recipientAccount = accounts.value.find(account => account.accountNumber === recipientAccountNumber.value);
 
      if (!senderAccount) {
        transferMessage.value = 'Sender account not found';
        return;
      }
 
      if (!recipientAccount) {
        transferMessage.value = 'Recipient account not found';
        return;
      }
 
      if (transferAmount.value <= 0) {
        transferMessage.value = 'Invalid transfer amount';
        return;
      }
 
      if (senderAccount.balance < transferAmount.value) {
        transferMessage.value = 'Insufficient funds';
        return;
      }
 
      senderAccount.balance -= transferAmount.value;
      recipientAccount.balance += transferAmount.value;
      transferMessage.value = `Successfully transferred $${transferAmount.value} to ${recipientAccount.accountHolder}`;
      transferAmount.value = 0;
      recipientAccountNumber.value = '';
    };
 
    return {
      accounts,
      transferAmount,
      recipientAccountNumber,
      transferMessage,
      transfer
    };
  }
};