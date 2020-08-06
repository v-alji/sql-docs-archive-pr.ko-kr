---
title: Reporting Services 스크립트 파일 실행 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c787d860838a57a2bd0f51aac1e9159833f038d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735976"
---
# <a name="run-a-reporting-services-script-file"></a><span data-ttu-id="4d573-102">Reporting Services 스크립트 파일 실행</span><span class="sxs-lookup"><span data-stu-id="4d573-102">Run a Reporting Services Script File</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4d573-103">스크립트 파일은 명령 프롬프트에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 스크립트 환경(RS.exe)을 사용하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-103">script files are run from the command prompt using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment (RS.exe).</span></span> <span data-ttu-id="4d573-104">RS.exe에는 사용할 수 있는 많은 명령 프롬프트 인수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-104">RS.exe has many command prompt arguments available for you to use.</span></span> <span data-ttu-id="4d573-105">명령 프롬프트 옵션에 대한 자세한 내용은 [RS.exe 유틸리티&#40;SSRS&#41;](rs-exe-utility-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d573-105">For more information about the command prompt options, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span> <span data-ttu-id="4d573-106">추가 스크립트 예제는 [SQL Server Reporting Services 제품 예제(SQL Server Reporting Services Product Samples)](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4d573-106">For more script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="sample-command-lines"></a><span data-ttu-id="4d573-107">예제 명령줄</span><span class="sxs-lookup"><span data-stu-id="4d573-107">Sample Command Lines</span></span>  
  
-   <span data-ttu-id="4d573-108">대상 보고서 서버를 지정하여 스크립트 환경에서 Script.rss를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-108">Run Script.rss in the script environment designating the target report server.</span></span> <span data-ttu-id="4d573-109">기본적으로 Windows 인증이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-109">Windows Authentication is applied by default:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   <span data-ttu-id="4d573-110">웹 서비스 호출을 인증하기 위한 사용자 이름과 암호를 지정하여 스크립트 환경에서 Script.rss를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-110">Run Script.rss in the script environment specifying a user name and password for authenticating the Web service calls:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   <span data-ttu-id="4d573-111">서버 제한 시간을 30초로 지정하여 스크립트 환경에서 Script.rss를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-111">Run Script.rss in the script environment specifying a server time-out of 30 seconds:</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   <span data-ttu-id="4d573-112">*report*라는 전역 스크립트 변수를 지정하여 스크립트 환경에서 Script.rss를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-112">Run Script.rss in the script environment specifying a global script variable called *report*.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   <span data-ttu-id="4d573-113">스크립트 파일의 웹 서비스 작업이 일괄 처리로 실행되도록 지정하여 스크립트 환경에서 Script.rss를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d573-113">Run Script.rss in the script environment specifying that the Web service operations in the script file are run as a batch.</span></span>  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4d573-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d573-114">See Also</span></span>  
 [<span data-ttu-id="4d573-115">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4d573-115">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
