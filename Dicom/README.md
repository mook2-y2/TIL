# Install dcmtk on Mac OSX
```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null

brew install dcmtk
```
- 참고 : http://macappstore.org/dcmtk/


# Encapsulated PDF 
- DICOM IOD 한 종류
- SOP Class UID : 1.2.840.10008.5.1.4.1.1.104.1
- PDF document that has been encapsulated within a DICOM Information Object.
- dcmtk의 pdf2dcm을 통해 만들 수 있으며, Horos Viewer를 통해 열 수 있음 (https://support.dcmtk.org/docs/pdf2dcm.html)
```bash
pdf2dcm [options] pdffile-in dcmfile-out
```
- PDF 뷰어에서도 열릴 수 있다고 한다. (https://www.radiantviewer.com/dicom-viewer-manual/encapsulated-pdf-documents.html) -> 실제로 Horos Viewer에서 더블클릭하면 PDF Viewer로 열리는 것 확인. 
- Encapsulated PDF의 태그에서 살펴볼만한 부분 
  - Document Title (0042,0010) : 제목이 되는 부분. 뷰어에서 더블 클릭으로 PDF Viewer로 여는 경우 파일 제목이 된다. 
  - Encapsulated Document (0042,0011) : Encapsulated Document IOD는 Pixel Data 태그가 없으며 원본 내용이 Encapsulated Document 태그에 담긴다. 
  - MIMETypeOfEncapsulatedDocument (0042,0012): Encapulated Dicom IOD의 타입 (PDF의 경우 application/pdf)

