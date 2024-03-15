Informational Issue

1.Use custom errors instead of require:
InterestRateModel.sol => require(owner() == _msgSender(), "Ownable: caller is not the owner");
InterestRateModel.sol => require(newOwner != address(0), "Ownable: new owner is the zero address");
  
2.Multiplication by two should use bit shifting:
InterestRateModel.sol => uint256 public constant MAX_MULTIPLIER_X96 = Q96 * 2; // 200%

3.Constants in comparisons should appear on the left side:
InterestRateModel.sol => require(newOwner != address(0), "Ownable: new owner is the zero address");
InterestRateModel.sol => if (debt == 0) {

4.Owner can renounce Ownership:
InterestRateModel.sol => function renounceOwnership() public virtual onlyOwner {

5.Large numeric literals should use underscores for readability:
InterestRateModel.sol => uint256 public constant YEAR_SECS = 31557600; // taking into account leap years

### Time spent:
18 hours