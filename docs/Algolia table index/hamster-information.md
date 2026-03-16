---
title: Hamster Information
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
<HTMLBlock>{`
<p>Hamster Wheel Device</p>
<table>
<thead>
<tr>
<th>Name</th>
<th>Display Name (EN-US)</th>
<th>Final Description</th>
<th>Is account parameter?</th>
<!-- <th>Brazil only</th> -->
<th>Program types</th>
<th>Required parameter (Credit)?</th>
<th>Required Parameter (Debit)?</th>
<th>Required parameter (Prepaid)?</th>
<th>Required parameter (Credit or Balance)?</th>
<th>Required parameter (Prepaid or Balance)?</th>
<th>Required parameter (Debit or Balance)?</th>
<th>Required parameter CONTA CORRENTE (Itaú Legacy)</th>
<th>Value type</th>
<th>Max length</th>
<th>Default value</th>
</tr>
</thead>
<tr class="odd">
<td>ALLOW_ACCOUNTS_CREATION</td>
<td>Enable accounts creation</td>
<td>Enable accounts creation</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT (required), PRE-PAID (required), DEBIT (required), CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE, CORPORATE</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>BOOLEAN</td>
<td></td>
<td>TRUE</td>
</tr>
<tr class="even">
<td>ALLOW ACCOUNTS SAME EXTERNAL ID</td>
<td>Allow account creation using existing <code>external_id</code></td>
<td>Allow account creation using an external account ID in the org</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>N/A</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>ALLOW MULTIPLE ACCOUNTS FOR CREDENTIAL</td>
<td>Allow <code>document_number</code> reuse</td>
<td>Allow multiple accounts to be created in a program with the same <code>document_number</code></td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>N/A</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="even">
<td>ALLOW NULL DOCUMENT</td>
<td>Allow creating entities without <code>document number</code></td>
<td>Allow creation of entities without a <code>document number</code> (when using a different identifier instead)</td>
<td>No</td>
<!-- <td>No</td> -->
<td></td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>ALLOW_BANK_ACCOUNT_CREATION</td>
<td>Allow account auto-creation</td>
<td>[ITI only) Automatically generate bank accounts upon account creation (unless overridden in the payload)</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="even">
<td>ENVIA SMS SENHA CARTAO</td>
<td>Allow sending card passwords via SMS</td>
<td>Allow sending card passwords to customers via SMS text message</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>EXTERNAL ID AS MAIN KEY</td>
<td>Use <code>external_id</code> as account ID</td>
<td>Use <code>external_id</code> parameter as main identifier for accounts</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td>Optional</td>
<td>FALSE</td>
</tr>
<tr class="even">
<td>GERA SENHA CARTAO</td>
<td>Generate random password on card creation</td>
<td>Generate random password for newly created card (user can only change afterward)</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>N/A</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td>Optional</td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>INTERVALO DIAS TROCA CAMBIO</td>
<td>Exchange rate expiration</td>
<td>Exchange rate expiration period (days)</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>LIMITE GLOBAL MAXIMO</td>
<td>Maximum credit limit</td>
<td>(Credit programs only) Overall maximum credit limit for credit accounts in the program</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>1000</td>
</tr>
<tr class="odd">
<td>LIMITE GLOBAL MINIMO</td>
<td>Minimum credit limit</td>
<td>(Credit programs only) Overall minimum credit limit for credit accounts in the program</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>LIMITE PROVISORIO</td>
<td>Provisional global limit</td>
<td>Overall limit for credit or debit accounts in the program</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Decimal</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>MAXIMO ADICIONAIS</td>
<td>Maximum number of card holders</td>
<td>Maximum number of additional card holder accounts in the program</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>INTEGER</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ONBOARDING_CARDS_CREATION</td>
<td>Create physical card when creating account</td>
<td>When creating an account, also create a physical card for the account owner</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>PERCENTUAL LIMITE GLOBAL</td>
<td>Percentage of income to be used as the global limit for account</td>
<td>Percentage of income to be used as global limit for account</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Decimal</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>PERCENTUAL LIMITE SAQUE</td>
<td>Withdrawal limit percentage</td>
<td>Maximum allowed amount for withdrawals and payments as a percentage of the maximum credit limit granted by the institution to users of this program.<br><strong>Note:</strong> This value is set in decimal places. For example, to set a withdrawal limit of 10%, use <code>0.1</code></td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>1</td>
</tr>
<tr class="odd">
<td>SEND PASSWORD VIA SMS</td>
<td>Send password via SMS</td>
<td>Allow sending passwords via SMS when creating an account</td>
<td>No</td>
<!-- <td>No</td> -->
<td></td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>TAMANHO MAX NOME EMBOSSADO</td>
<td>Max name length on physical card</td>
<td>Maximum number of characters for the cardholder's name on a pphysical card</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>25</td>
</tr>
<tr class="odd">
<td>TARIFA EXTRATO CORREIO</td>
<td>Mailed statements fee</td>
<td>Fee for mailing a paper statement</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>DECIMAL</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>ALLOW TOKENIZED TRANSACTION WITH CREATED CARD</td>
<td>Allow tokenized transactions with new card on file</td>
<td>Allow card not present (CNP) transactions with cards in CREATED status (but not yet activated)</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Required</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>APPROVE_RULES_AUTHORIZATION_PARAMETER</td>
<td>Approve rules authorization</td>
<td>If spending controls are configured for the program, authorize transactions by default if the response from the rules-api contains an error</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CONTA CORRENTE</td>
<td>Optional</td>
<td>Required</td>
<td>Optional</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>APPROVE_RULES_CANCELLATION_PARAMETER</td>
<td>Approve rules cancellation</td>
<td>Refuse transactions by default if Rules API is unavailable</td>
<td>No</td>
<!-- <td>No</td> -->
<td></td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>ATC MAX OFFSET</td>
<td>ATC maximum offset</td>
<td>When comparing the current ATC value received with the values registered in our database) the difference must be less than this value</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>INTEGER</td>
<td></td>
<td>15</td>
</tr>
<tr class="even">
<td>ATC MIN OFFSET</td>
<td>ATC minimum offset</td>
<td>When comparing the current ATC value received with the values registered in our database, the difference must be greater than this value</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>INTEGER</td>
<td></td>
<td>5</td>
</tr>
<tr class="odd">
<td>AUTORIZACAO INTERNA</td>
<td>Internal authorizations</td>
<td>Allow override of issuer's denial. This allows adaptation to different compliance rules or to create an extra layer of security</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>1</td>
</tr>
<tr class="even">
<td>IOF INTERNACIONAL</td>
<td>IOF international fee</td>
<td>[Brazil only] Fee for international purchases</td>
<td>Yes</td>
<!-- <td>Yes</td> -->
<td>CREDIT, PRE-PAID, DEBIT</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>DECIMAL</td>
<td></td>
<td>6.38</td>
</tr>
<tr class="odd">
<td>LIMITE TRANSACOES CARTAO TEMPORARIO</td>
<td>Limit transactions for temporary cards</td>
<td>Transaction limit amount for temporary cards. The amount on the card is renewed every time the Issuer renews the card. Counts only authorized transactions</td>
<td>No</td>
<!-- <td>No</td> -->
<td></td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>INTEGER</td>
<td></td>
<td>14</td>
</tr>
<tr class="even">
<td>SEND_RULES_AUTHORIZATION_PARAMETER</td>
<td>Send rules authorization</td>
<td>If spending controls are configured, evaluate rules using either Rules API (default) or with some other rules. To call rules v1 endpoint, set value to \`2\`; to call rules v2 endpoint, set value to \`1\`</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>INTEGER</td>
<td></td>
<td>2</td>
</tr>
<tr class="odd">
<td>TENTATIVAS SENHA ERRADA</td>
<td>Wrong password attempts</td>
<td>Number of wrong password attempts allowed before blocking the card</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>Required</td>
<td>INTEGER</td>
<td></td>
<td>3</td>
</tr>
<tr class="even">
<td>ACCRUAL RATE DISCOUNT</td>
<td>Accrual rate discount</td>
<td>[Brazil only] Discount on OVERDUE and REFINANCING accruals. Does not apply to IOF</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>ACCRUAL_CALC_STRATEGY</td>
<td>Accrual calculation strategy</td>
<td>Parameter to define the start date for daily accruals: 0 - Normal (Due Date +1) / 1 - Calculation goes back to debit’s date (first installment: transaction date + 1; other installments: corresponding cycle start date + 1).
</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>ACCRUAL_PROJECTION_STRATEGY</td>
<td>Accrual projection calculation method</td>
<td>0 = Disabled, 1 = LINEAR PROJECTION (accruals projected from cycle closing to due date)</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>CONTROLE DE TROCA DE VENCIMENTOS</td>
<td>Due date exchange control</td>
<td>Flag for validating the change of expiration dates. If TRUE, you cannot change the due date more than once per cycle. Valid only if <code>STANDARD CALENDAR SELECTION = false</code></td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>1 (true)</td>
</tr>
<tr class="even">
<td>DIAS ANTECEDENCIA CORTE</td>
<td>Statement closing date</td>
<td>Number of days before due date to set statement closing date</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>10</td>
</tr>
<tr class="odd">
<td>DIAS ATRASO BLOQUEIO CONTA</td>
<td>Block account for late payment</td>
<td>Number of days after due date to block account for nonpayment</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>10</td>
</tr>
<tr class="even">
<td>DIAS VENCIMENTO BOLETO</td>
<td>Delayed payment period for boleto (bank slip)/td>
<td>[Brazil only] Delayed payment # of days for boleto. Calculated either by Due Date or by Real Due Date (if due date falls on a holiday or weekend)</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>5</td>
</tr>
<tr class="odd">
<td>IOF DIARIO</td>
<td>IOF daily rate</td>
<td>[Brazil only] IOF daily tax rate on a credit operation (revolving, installment billing and invoice settlement)</td>
<td>Yes</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>0,0082</td>
</tr>
<tr class="even">
<td>IOF FIXO</td>
<td>IOF monthly fee</td>
<td>[Brazil only] IOF monthly fee on a credit operation (revolving, invoice installment and invoice agreement)</td>
<td>Yes</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td></td>
<td></td>
<td></td>
<td>DECIMAL</td>
<td></td>
<td>0.38</td>
</tr>
<tr class="odd">
<td>IOF_FIRST_DAY</td>
<td>IOF first day</td>
<td>[Brazil only] Revolving IOF charge on unpaid debit balance occurs on the first day of the month</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>MIN_PAYMENT_CALC_STRATEGY</td>
<td>Minimum payment calculation method</td>
<td>Method for calculating minimum amount due. 0 = Brazil model: 100% outstanding balance of previous statements + percentage of statement transactions prior to cycle closing<br />
1 = Argentina model: Percentage of all transactions prior to cycle closing<br />
2 = India model: 100% of outstanding overdue and overlimit amounts</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>MINIMO BOLETO</td>
<td>Minimum boleto</td>
<td>[Brazil only] When statement amount is less than value configured as MINIMO BOLETO, outstanding balance does not accrue interest</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>NON_BUSINESS_DAYS</td>
<td>Non-business days</td>
<td>Days of the week to be considered non-business days: 1 = Monday, 2 = Tuesday, 3 = Wednesday, 4 = Thursday, 5 = Friday, 6 = Saturday, 7 = Sunday</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td>n/a</td>
<td>67</td>
</tr>
<tr class="odd">
<td>NUMERO MAXIMO PARCELAS REFINANCIAMENTO</td>
<td>Maximum refinancing installments (v2 and v3 endpoints only)</td>
<td>Maximum number of installments allowed in a refinancing agreement (v2 and v3 endpoints)</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>18</td>
</tr>
<tr class="even">
<td>OVERDUE_ACCRUAL_CALC_STRATEGY</td>
<td>Overdue fee calculation method</td>
<td>0 = fee applied to 100% of remaining overdue balance; 1 = fee applied to minimum payment of overdue balance</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>OVERLIMIT_FEE_AMOUNT</td>
<td>Overlimit fee amount</td>
<td>Fee applied if the customer exceeds the card limit (if allowed for the account). This fee is charged at the end of the invoice cycle.</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>PARCELAS ANUIDADE</td>
<td>Annuity installments</td>
<td>Number of installments to pay annuity. When parameterized, automatically divides value of annuity into number of installments. Creates transaction of type <code>Annuity</code> in customer statement.</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>PERCENTUAL MAXIMO ENTRADA ACORDO FATURA</td>
<td>Maximum percentage of first payment</td>
<td>Maximum percentage of first payment to effect a statement agreement (v2 and v3 endpoints only).</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>90</td>
</tr>
<tr class="even">
<td>PERCENTUAL MINIMO ENTRADA ACORDO FATURA</td>
<td>Minimum percentage of first payment</td>
<td>Minimum percentage of first payment to effect statement agreement (v2 and v3 endpoints only)</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>10</td>
</tr>
<tr class="odd">
<td>STOP ACCRUAL</td>
<td>Stop accrual # of days</td>
<td>Maximum days in arrears for which the calculation of fees, interest ,and fines will be posted. The platform won’t post any accrued amount that was calculated after the STOP_ACCRUAL number of days. (You can still post these accruals manually using the Statements API.)</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td>-</td>
<td>63</td>
</tr>
<tr class="even">
<td>TAXA REFINANCIAMENTO FATURA</td>
<td>Statement balance refinancing rate</td>
<td>Rate for refinancing a statement balance (v2 and v3 endpoints only)</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td>-</td>
<td>5.99</td>
</tr>
<tr class="odd">
<td>VALOR ANUIDADE</td>
<td>Annuity fee amount</td>
<td>Fee charged per annuity on account anniversary. Must be configured in conjunction with the <code>Annuity Installment</code> parameter. It is related to parameter <code>PARCELAS ANUIDADE</code>.</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Decimal</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>VALOR MAXIMO ENTRADA ACORDO FATURA</td>
<td>Maximum amount entered according to invoice</td>
<td>Maximum amount for first payment in execution of statement agreement (v2 and v3 agreement endpoints only)</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Decimal</td>
<td>-</td>
<td>30000000</td>
</tr>
<tr class="odd">
<td>VALOR MINIMO ENTRADA ACORDO FATURA</td>
<td>Minimum down payment</td>
<td>Minimum down payment amount for effecting a payment agreement (v2 and v3 endpoints only)</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Decimal</td>
<td>-</td>
<td>15</td>
</tr>
<tr class="even">
<td>VALOR MINIMO PARCELA ACORDO FATURA</td>
<td>Minimum installment payment</td>
<td>Minimum payment amount for each installment of a payment agreement (v2 and v3 endpoints only)</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Decimal</td>
<td>-</td>
<td>15</td>
</tr>
<tr class="odd">
<td>VALOR MINIMO PARCELA REFINANCIAMENTO</td>
<td>Minimum installment value (payment refinancing)</td>
<td>Minimum payment amount for each installment of refinancing agreement (v2 and v3 endpoints only)</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Decimal</td>
<td>-</td>
<td>7</td>
</tr>
<tr class="even">
<td>CONTRACT_BIND_ALLOWED</td>
<td>Contract bind allowed</td>
<td>Allows a contract to be bound to an account from a specific program</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td>N/A</td>
<td>0</td>
</tr>
<tr class="odd">
<td>DESCONTO ITAU</td>
<td>Itaú transfer discount</td>
<td>[Itaú only] Used to apply discount on specific Itaú transfer flows</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>DECIMAL</td>
<td>N/A</td>
<td>0</td>
</tr>
<tr class="even">
<td>PERMITIDO P2P/CASHIN</td>
<td>Allow transfer/cash-in</td>
<td>Allow accounts to receive funds via transfer/cashin</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>ACCEPT_MULTIPLE_PLASTIC_CARDS</td>
<td>Allow multiple physical cards</td>
<td>Allow more than one physical card to draw from the same available balance</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>(0) FALSE</td>
</tr>
<tr class="even">
<td>ALLOW EARMARKING</td>
<td>Allow earmarking</td>
<td>Allow earmarking (set aside some amount of money from the total funds for later use)</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>BOOLEAN</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>EMBOSSA CARTAO ADICIONAL</td>
<td>Emboss additional card</td>
<td>(Private label cards only) Allow sending an additional card to embossing</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="even">
<td>EMBOSSA CARTAO SEM ENDERECO</td>
<td>Emboss card with no address</td>
<td>Allow cards sent for embossing to exclude address information</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>NUMERO MESES EXPIRACAO CARTAO</td>
<td>Card expiration (# of months)</td>
<td>Number of months to add to the current date when setting card expiration period</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE</td>
<td>Optional</td>
<td>Optional</td>
<td>Optional</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>72</td>
</tr>
<tr class="even">
<td>SKIP_RENEW_TEMPORARY_CARD</td>
<td>Skip auto-renewal of temporary cards</td>
<td>By default, a temporary card is automatically renewed (after the PCI data is checked). When TRUE, temporary card auto-renewal is skipped.</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE</td>
<td>Optional</td>
<td>Optional</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Optional</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>PERCENTUAL LIMITE PARCELA</td>
<td>Installment limit percentage</td>
<td>Installment limit as a percentage of global limit</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>DECIMAL</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>PERCENTUAL LIMITE PARCELADO</td>
<td>Percentual limite parcelado</td>
<td>Installment limit as a percentage of global limit</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ACCRUALS_REVERSAL_STRATEGY</td>
<td>Accrual reversal strategy</td>
<td>Defines the accrual reversal strategy for purchase cancellations</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>DELINQUENCY_BUCKET_CALC_STRATEGY</td>
<td>Defines whether delinquency buckets should be calculated</td>
<td>Define whether delinquency buckets should be calculated for tracking account's debt; 0 = Do not calculate (Default); 1 = Calculate and amortize buckets from oldest to newest</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td></td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>ACCRUAL_PROJECTION_REVERSAL</td>
<td>Interest projection reversal</td>
<td>Defines whether the projected interest between the cut (closing) and the due date of the invoice should be reversed if a payment occurs before the due date.<br />
0 = Default (do not reverse)<br />
1 = Reverse</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td></td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td>0</td>
</tr>
<tr class="even">
<td>MDR</td>
<td>Merchant discount rate</td>
<td>Merchant discount rate (prepayment discount percentage for merchants)</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>INTEGER</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>MIN SAVINGS APPLICATION</td>
<td>Minumum deposit amount</td>
<td>For an interest-bearing account, accrual adjustments depend on interest rate and period rules. By establishing a minimum amount to be applied, a minimum amount is required for each deposit</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>Optional</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>100</td>
</tr>
<tr class="even">
<td>OPTIN SAVING ACCOUNT</td>
<td>Opt-in savings account</td>
<td>Flag indicating whether the account is an interest-bearing account</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>Optional</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td>FALSE</td>
</tr>
<tr class="odd">
<td>GRACE_PERIOD_ADDITIONAL_NR_OF_DAYS</td>
<td>Number of grace days granted to the program</td>
<td>Add this number of grace days to the original grace period. Valid values are from 0 to 10</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td>-</td>
<td>0</td>
</tr>
<tr class="even">
<td>Accounting_MDR</td>
<td>Accounting MDR</td>
<td>[Itaú - Brazil only] MDR (merchant discount rate) -- Prepayment discount percentage for merchants</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Optional</td>
<td>PERCENTAGE</td>
<td></td>
<td>0,0000</td>
</tr>
<tr class="odd">
<td>Accounting_RAV</td>
<td>Accounting RAV</td>
<td>[Itaú - Brazil only] RAV (prepayment of receivables) -- Prepayment discount percentage for prepayment of credit card settlements</td>
<td>No</td>
<!-- <td>Yes</td> -->
<td>CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Optional</td>
<td>PERCENTAGE</td>
<td></td>
<td>0,0000</td>
</tr>
<tr class="even">
<td>DIFOP</td>
<td>DIFOP</td>
<td>[Itaú - Brazil only] Refers to revenue from overdue charges up to 59 days</td>
<td>No</td>
<!-- <td>No</td> -->
<td>CREDIT</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>Optional</td>
<td>DECIMAL</td>
<td></td>
<td>0,0000</td>
</tr>
<tr class="odd">
<td>ENVIA EMAIL PAGAMENTO</td>
<td>Send email upon payment</td>
<td>Send email notifications upon processing any bank/gateway/authorizer payment</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ENVIA SMS PAGAMENTO</td>
<td>Send SMS upon payment</td>
<td>Send SMS notifications upon processing any bank/gateway/authorizer payment</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>BOOLEAN</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>TIMELINE_CATEGORY</td>
<td>Timeline Category display name</td>
<td>Display name for the <code>Category</code> field of a timeline</td>
<td>No</td>
<!-- <td>No</td> -->
<td></td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>TIMELINE_TYPE</td>
<td>Timeline Type display name</td>
<td>Display name for the <code>Type</code> field of a timeline</td>
<td>No</td>
<!-- <td>No</td> -->
<td></td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>INTEGER</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>VALOR MAXIMO CARGA</td>
<td>Maximum recharge value</td>
<td>Maximum recharge amount</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>Optional</td>
<td>N/A</td>
<td>Optional</td>
<td>N/A</td>
<td>Optional</td>
<td>DECIMAL</td>
<td></td>
<td>2500</td>
</tr>
<tr class="even">
<td>VALOR MINIMO CARGA</td>
<td>Minimum recharge value</td>
<td>Minimum recharge amount</td>
<td>Yes</td>
<!-- <td>No</td> -->
<td>CREDIT, PRE-PAID, DEBIT, CREDIT ZERO-BALANCE, PRE-PAID ZERO-BALANCE, DEBIT ZERO-BALANCE, CONTA CORRENTE</td>
<td>N/A</td>
<td>N/A</td>
<td>Optional</td>
<td>N/A</td>
<td>Optional</td>
<td>N/A</td>
<td>Optional</td>
<td>DECIMAL</td>
<td></td>
<td>0</td>
</tr>
<tr class="odd">
<td>LATE_PAYMENT_FEE</td>
<td>Late payment fee</td>
<td>Percentage used to calculate and post a transaction at each cycle closing if the rules are satisfied</td>
<td>No</td>
<!-- <td>No</td> -->
<td></td>
<td>Required</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>DECIMAL</td>
<td></td>
<td>0</td>
</tr>
</tbody>
</table>
`}</HTMLBlock>
