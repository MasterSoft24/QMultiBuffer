## QMultiBuffer

QMultiBuffer is a QIODevice-based class for easy working with a few byte-streams as with single. Data sources may be  QIODevice-based objects (QFile, QTctSocket and so on), QByteArrays. This class let you merge few sources into one data stream and works with it as with standard IO-device.

### Example

***

	QMultiBuffer mb;
	QByteArray ba("This is a first data stream");
	QFile f("/path/to/file"); // let a file contains string "This is a file contents"
	
	mb.append(&ba);
	mb.append(&f);
	mb.append(&ba);
	
	mb.open(QIODevice::ReadOnly);
	
	qDebug() << mb.readAll();
	
	mb.seek(10);
	
	qDebug() << mb.read(10);
	
	// a as result we get a two string "This is a first data streamThis is a file contentsThis is a first data stream"
	// and "first data"
