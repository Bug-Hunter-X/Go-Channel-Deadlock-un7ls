# Go Channel Deadlock

This repository demonstrates a potential deadlock scenario in Go using channels and goroutines.  The program involves a writer goroutine sending values to a channel and a reader goroutine receiving those values. Under certain circumstances, this can lead to a deadlock if the reader tries to read from a closed channel.

## Problem Description

A race condition exists between the writer closing the channel and the reader finishing. If the writer closes the channel before the reader has consumed all the values, and the reader tries to read from the closed channel again after it has processed the values in the channel, it will block indefinitely, which leads to a deadlock. 

## Solution

The solution addresses the potential deadlock by ensuring proper synchronization between the writer and the reader goroutines. The solution includes checking the channel close signal, which prevents potential deadlocks.