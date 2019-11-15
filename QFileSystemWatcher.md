# QFileSystemWatcher

## MyFileWatcher.h

#ifndef MYFILEWATCHER_H
#define MYFILEWATCHER_H

#include <QObject>
#include <QFileSystemWatcher>

class MyFileWatcher : public QObject
{
    Q_OBJECT
public:
    explicit MyFileWatcher(QObject *parent = nullptr);

public slots:
    void onFileChanged(const QString &file);
    void onDirectoryChanged(const QString &path);

private:
    QFileSystemWatcher m_fileWatcher;
};

#endif // MYFILEWATCHER_H

## MyFileWatcher.cpp


#include "MyFileWatcher.h"
#include <QDebug>

MyFileWatcher::MyFileWatcher(QObject *parent) : QObject(parent)
{
    m_fileWatcher.addPath("C:/Documents/test.txt"); // monitoring file
    m_fileWatcher.addPath("C:/Documents/test"); // monitoring directory

    connect(&m_fileWatcher, SIGNAL(fileChanged(const QString&)), this, SLOT(onFileChanged(const QString &)));
    connect(&m_fileWatcher, SIGNAL(directoryChanged(const QString&)), this, SLOT(onDirectoryChanged(const QString &)));

    qDebug()<<"Monitoring File:"<<m_fileWatcher.files();
    qDebug()<<"Monitoring Directory:"<<m_fileWatcher.directories();
}

void MyFileWatcher::onFileChanged(const QString &file)
{
    qDebug()<<"File Changed:"<<file;
}

void MyFileWatcher::onDirectoryChanged(const QString &path)
{
    qDebug()<<"Directory Changed:"<<path;
}
