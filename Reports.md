https://github.com/dark0rder/wise-lending-codebase-code4rena/blob/gurvinder/contracts/WiseLending.sol#L254-L268
https://github.com/dark0rder/wise-lending-codebase-code4rena/blob/gurvinder/contracts/WiseLendingDeclaration.sol#L300
https://github.com/dark0rder/wise-lending-codebase-code4rena/blob/gurvinder/contracts/WiseLendingDeclaration.sol#L322-L325

( i am not sure about this ) ---> Doubts
this function _getCurrentSharePriceMax might  return incorrect APR.

  return timeDifference
            * RESTRICTION_FACTOR
            + PRECISION_FACTOR_E18;

  // APR RESTRICTIONS
    uint256 internal constant RESTRICTION_FACTOR = 10
        * PRECISION_FACTOR_E36
        / PRECISION_FACTOR_YEAR;

        uint256 internal constant PRECISION_FACTOR_YEAR = PRECISION_FACTOR_E18 * ONE_YEAR;
          uint256 internal constant ONE_YEAR = 365 days;

Vul Details::

A leap year is a year with 366 days instead of the usual 365. 
This additional day is added to February, 
making it 29 days long instead of 28. 
Leap years occur approximately every four years.

If it brings inAacurate APR, it can affect other functions  for caculating the yearly interest rate for borrowers and lenders
so borrowers might have to pay high interests on their loans.
