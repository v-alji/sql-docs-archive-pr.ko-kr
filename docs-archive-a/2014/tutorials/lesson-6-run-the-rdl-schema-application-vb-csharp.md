---
title: '6 단원: RDL 스키마 응용 프로그램 실행 (VB-C #) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5a0fc2cd9c12b4b1602f517dc215ca44e686c663
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727491"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a><span data-ttu-id="eccd5-102">6 단원: RDL 스키마 응용 프로그램 실행 (VB-C #)</span><span class="sxs-lookup"><span data-stu-id="eccd5-102">Lesson 6: Run the RDL Schema Application (VB-C#)</span></span>
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]<span data-ttu-id="eccd5-103">에서는 다음과 같이 IDE(통합 개발 환경)에서 콘솔 애플리케이션을 작성하고 실행하는 두 가지 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eccd5-103">offers two methods to build and run a console application from the integrated development environment (IDE):</span></span>  
  
-   <span data-ttu-id="eccd5-104">디버깅으로 시작</span><span class="sxs-lookup"><span data-stu-id="eccd5-104">Start (with Debugging)</span></span>  
  
-   <span data-ttu-id="eccd5-105">디버깅하지 않고 시작</span><span class="sxs-lookup"><span data-stu-id="eccd5-105">Start without Debugging</span></span>  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a><span data-ttu-id="eccd5-106">SampleRDLSchema 애플리케이션을 작성하고 실행하려면</span><span class="sxs-lookup"><span data-stu-id="eccd5-106">To build and run the SampleRDLSchema application</span></span>  
  
1.  <span data-ttu-id="eccd5-107">**디버그** 메뉴에서 **디버깅하지 않고 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eccd5-107">From the **Debug** menu, click **Start Without Debugging**.</span></span> <span data-ttu-id="eccd5-108">이렇게 하면 프로그램이 실행을 마친 후에도 콘솔 창이 열린 채로 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eccd5-108">This ensures that the console window remains open after the program has finished executing.</span></span>  
  
     <span data-ttu-id="eccd5-109">애플리케이션은 다음 결과를 콘솔로 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="eccd5-109">The application prints the following output to the console:</span></span>  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  <span data-ttu-id="eccd5-110">아무 키나 눌러 콘솔을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="eccd5-110">Press any key to close the console.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eccd5-111">발생하는 모든 오류는 콘솔에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="eccd5-111">Any errors that occur are written to the console.</span></span>  
  
3.  <span data-ttu-id="eccd5-112">예제 애플리케이션이 실행을 마치면 보고서의 업데이트된 복사본이 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="eccd5-112">When the sample application is finished running an updated copy of the report will be saved to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eccd5-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eccd5-113">See Also</span></span>  
 <span data-ttu-id="eccd5-114">[RDL 스키마 &#40;생성 된 클래스를 사용 하 여 보고서 업데이트 (SSRS 자습서&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="eccd5-114">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="eccd5-115">보고서 정의 언어&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="eccd5-115">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
