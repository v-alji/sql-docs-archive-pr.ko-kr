---
title: '3 단원: 보고서 서버에서 보고서 정의 로드 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc6ed26703599792b9c739f8d185ae4f190fc8be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649877"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a><span data-ttu-id="10e19-102">3단원: 보고서 서버에서 보고서 정의 로드</span><span class="sxs-lookup"><span data-stu-id="10e19-102">Lesson 3: Load a Report Definition from the Report Server</span></span>
  <span data-ttu-id="10e19-103">프로젝트를 만들고 RDL 스키마에서 클래스를 생성하면 보고서 서버에서 보고서 정의를 로드할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10e19-103">After you have created your project and generated the classes from the RDL schema, you are ready to load a report definition from the report server.</span></span>  
  
### <a name="to-load-a-report-definition"></a><span data-ttu-id="10e19-104">보고서 정의를 로드하려면</span><span class="sxs-lookup"><span data-stu-id="10e19-104">To load a report definition</span></span>  
  
1.  <span data-ttu-id="10e19-105">클래스의 맨 위에 `ReportUpdater` (를 사용 하는 경우 모듈) 전용 필드를 추가 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Report` 합니다.</span><span class="sxs-lookup"><span data-stu-id="10e19-105">Add a private field at the top of the `ReportUpdater` class (module if you are using [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) for the `Report` class.</span></span> <span data-ttu-id="10e19-106">이 필드는 애플리케이션의 수명이 지속되는 동안 보고서 서버에서 로드된 보고서에 대한 참조를 유지 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10e19-106">This field will be used to maintain a reference to report that is loaded from the report server for the life of the application.</span></span>  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  <span data-ttu-id="10e19-107">Program.cs 파일([!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 경우 Module1.vb)에서 `LoadReportDefinition()` 메서드의 코드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="10e19-107">Replace the code for the `LoadReportDefinition()` method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report definition   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report definition   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="10e19-108">다음 단원</span><span class="sxs-lookup"><span data-stu-id="10e19-108">Next Lesson</span></span>  
 <span data-ttu-id="10e19-109">다음 단원에서는 코드를 작성하여 보고서 서버에서 로드된 보고서 정의를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="10e19-109">In the next lesson, you will write code to update the report definition that was loaded from the report server.</span></span> <span data-ttu-id="10e19-110">[4 단원: 프로그래밍 방식으로 보고서 정의 업데이트를](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10e19-110">See [Lesson 4: Update the Report Definition Programmatically](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e19-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10e19-111">See Also</span></span>  
 <span data-ttu-id="10e19-112">[RDL 스키마 &#40;생성 된 클래스를 사용 하 여 보고서 업데이트 (SSRS 자습서&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="10e19-112">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="10e19-113">보고서 정의 언어&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="10e19-113">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
