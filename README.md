# StrikeRegister
This class implements anti-replay protection and compression for nonces.

Replay refers to tampering where datagrams are replayed.  The receiver must keep a record of datagrams it has received in order to avoid accepting the same datagram twice.  It is designed for nonce sequence numbers that start at 0 and increment by 1 for each datagram (reliable or unreliable).

IsDuplicate() checks incoming datagram nonces to see if they have already been seen.  Accept() will slide the window as needed and strike the nonce.

This implementation of sliding window anti-replay protection avoids actually shifting the bitfield window as an optimization.  Instead WindowBitRotation is incremented in place of a shift.

StrikeRegister will also decompress incoming nonce values from 1-7 bytes back to the original 8 byte (64-bit) sequence number based on recent values.

# SimpleCipher
This is a toy encryption scheme that looks random on the wire.  Its main goal is to be a fast obfuscator.


## Credits
Software by Christopher A. Taylor mrcatid@gmail.com

Please reach out if you need support or would like to collaborate on a project.
