
采用 fingerprint 作为 uuid，由客户端生成，因此没有必要单独保存 AnonymousUsers.

在 AnonymousRooms，AnonymousSessions 中保存有 user uuid 即可。

todo:

    已经不再生成 AnonymousUsers 记录，因此可以删除该功能了。


