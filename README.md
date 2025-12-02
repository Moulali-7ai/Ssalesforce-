trigger LoanApplicationTrigger on Loan_Application__c (
    before insert, 
    before update, 
    after insert, 
    after update
) {
    if (Trigger.isBefore) {
        if (Trigger.isInsert) {
            LoanApplicationHandler.beforeInsert(Trigger.new);
        }
        if (Trigger.isUpdate) {
            LoanApplicationHandler.beforeUpdate(Trigger.new, Trigger.oldMap);
        }
    } else if (Trigger.isAfter) {
        if (Trigger.isInsert) {
            LoanApplicationHandler.afterInsert(Trigger.new);
        }
        if (Trigger.isUpdate) {
            LoanApplicationHandler.afterUpdate(Trigger.new, Trigger.oldMap);
        }
    }
}

