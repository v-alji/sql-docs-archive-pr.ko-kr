---
title: '4 단원: 프로그래밍 방식으로 보고서 정의 업데이트 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1f0a1d46-6d6d-4f67-b51e-06dbbbffacf9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c090fc023e3ac47927b99ab61a45fd8ca2c79321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649864"
---
# <a name="lesson-4-update-the-report-definition-programmatically"></a><span data-ttu-id="306b2-102">4단원: 프로그래밍 방식으로 보고서 정의 업데이트</span><span class="sxs-lookup"><span data-stu-id="306b2-102">Lesson 4: Update the Report Definition Programmatically</span></span>
  <span data-ttu-id="306b2-103">이제 보고서 서버에서 보고서 정의가 로드되었고 보고서 필드를 사용하여 해당 정의를 참조했으므로 보고서 정의를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="306b2-103">Now that the report definition has been loaded from the report server and you have a reference to it using the report field, you need to update the report definition.</span></span> <span data-ttu-id="306b2-104">이 예에서는 보고서의 `Description` 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="306b2-104">For this example, you will update the `Description` property for the report.</span></span>  
  
### <a name="to-update-the-report-definition"></a><span data-ttu-id="306b2-105">보고서 정의를 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="306b2-105">To update the report definition</span></span>  
  
1.  <span data-ttu-id="306b2-106">Program.cs 파일 (의 경우 module1.vb)에서 UpdateReportDefinition () 메서드에 대 한 코드를 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="306b2-106">Replace the code for the UpdateReportDefinition() method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void UpdateReportDefinition()  
    {  
        System.Console.WriteLine("Updating Report Definition");  
  
        // Create a list of the Items Choices for the Report. The   
        // ItemsChoiceType118 enum represents all the properties  
        // available in the report and the ItemsElementName   
        // represents the properties that exist in the current   
        // instance of the report.  
        List<ItemsChoiceType118> _reportItems =   
            new List<ItemsChoiceType118>(_report.ItemsElementName);  
  
        // Locate the index for the Description property  
        int index = _reportItems.IndexOf(  
            ItemsChoiceType118.Description);  
  
        // The Description item is of type StringLocIDType, so   
        // cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
  
        // Update the Description for the Report  
        ((StringLocIDType)_report.Items[index]).Value =   
            "New Report Description";  
  
        System.Console.WriteLine("- New Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
    }  
    ```  
  
    ```vb  
    Private Sub UpdateReportDefinition()  
  
        System.Console.WriteLine("Updating Report Definition")  
  
        'Create a list of the Items Choices for the Report. The   
        'ItemsChoiceType118 enum represents all the properties  
        'available in the report and the ItemsElementName   
        'represents the properties that exist in the current   
        'instance of the report.  
        Dim reportItems As List(Of ItemsChoiceType118) = _  
            New List(Of ItemsChoiceType118)(m_report.ItemsElementName)  
  
        'Locate the index for the Description property  
        Dim index As Integer = _  
            reportItems.IndexOf(ItemsChoiceType118.Description)  
  
        'The Description item is of type StringLocIDType, so   
        'cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
        'Update the Description for the Report  
        DirectCast(m_report.Items(index), StringLocIDType).Value = _  
            "New Report Description"  
  
        System.Console.WriteLine("- New Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="306b2-107">다음 단원</span><span class="sxs-lookup"><span data-stu-id="306b2-107">Next Lesson</span></span>  
 <span data-ttu-id="306b2-108">다음 단원에서는 업데이트된 보고서 정의를 다시 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="306b2-108">In the next lesson, you will save the updated report definition back to the report server.</span></span> <span data-ttu-id="306b2-109">[5 단원: 보고서 정의를 보고서 서버에 게시를](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="306b2-109">See [Lesson 5: Publish the Report Definition to the Report Server](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306b2-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="306b2-110">See Also</span></span>  
 [<span data-ttu-id="306b2-111">RDL 스키마 &#40;생성 된 클래스를 사용 하 여 보고서 업데이트 (SSRS 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="306b2-111">Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)  
  
  
