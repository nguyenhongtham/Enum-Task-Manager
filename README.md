# Enum-Task-Manager
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract TaskManager {
    enum Status { Pending, InProgress, Completed, Cancelled }

    struct Task {
        string title;
        Status status;
        address assignee;
    }

    Task[] public tasks;

    function createTask(string memory _title, address _assignee) public {
        tasks.push(Task(_title, Status.Pending, _assignee));
    }

    function updateStatus(uint256 _id, Status _status) public {
        tasks[_id].status = _status;
    }

    function getTask(uint256 _id) public view returns (string memory, Status, address) {
        Task memory t = tasks[_id];
        return (t.title, t.status, t.assignee);
    }

    function taskCount() public view returns (uint256) {
        return tasks.length;
    }
}
