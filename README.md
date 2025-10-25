# Deploying-to-a-Testnet-Exercise
For base guild
Deploying to a Testnet Pin contract address:	0x075eB9Dc52177Aa3492E1D26f0fDE3d729625d2F

Simple contract code:

// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.23;

interface IBasicContractTest {
    function adder(
        uint _a,
        uint _b
    ) external returns (uint result, bool success);

    function subtractor(
        uint _a,
        uint _b
    ) external returns (uint result, bool success);
}

contract SafeMathContract is IBasicContractTest {
    function adder(
        uint _a,
        uint _b
    ) external pure override returns (uint result, bool success) {
        if (type(uint).max - _a < _b) {
            return (0, true);
        } else {
            result = _a + _b;
            return (result, false);
        }
    }

    function subtractor(
        uint _a,
        uint _b
    ) external pure override returns (uint result, bool success) {
        if (_b > _a) {
            return (0, true);
        } else {
            result = _a - _b;
            return (result, false);
        }
    }
}
