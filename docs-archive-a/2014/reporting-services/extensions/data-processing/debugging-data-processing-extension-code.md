---
title: 데이터 처리 확장 프로그램 코드 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bf7490145f91ee8b3cfc2357c34010bed593ed9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649935"
---
# <a name="debugging-data-processing-extension-code"></a><span data-ttu-id="85a86-102">데이터 처리 확장 프로그램 코드 디버깅</span><span class="sxs-lookup"><span data-stu-id="85a86-102">Debugging Data Processing Extension Code</span></span>
  <span data-ttu-id="85a86-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]에서는 데이터 처리 확장 프로그램 코드를 분석하여 오류를 찾는 데 유용한 디버깅 도구를 다수 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your data processing extension code and locate errors in it.</span></span> <span data-ttu-id="85a86-104">작업하기 가장 좋은 도구는 수행하려는 작업에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="85a86-105">이 예에서는 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-data-processing-extension-code"></a><span data-ttu-id="85a86-106">데이터 처리 확장 프로그램 코드를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="85a86-106">To debug your data processing extension code</span></span>  
  
1.  <span data-ttu-id="85a86-107">[!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]를 시작하고 데이터 처리 확장 프로그램 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)], and open your data processing extension project.</span></span>  
  
2.  <span data-ttu-id="85a86-108">프로젝트를 빌드하고 데이터 처리 확장 프로그램 어셈블리 및 해당하는 .pdb 파일을 보고서 디자이너에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-108">Build the project, and deploy your data processing extension assembly and the accompanying .pdb file to the Report Designer.</span></span> <span data-ttu-id="85a86-109">배포에 대 한 자세한 내용은 [방법: 보고서 디자이너에 데이터 처리 확장 프로그램 배포](deploying-a-data-processing-extension-to-report-designer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85a86-109">For more information about deployment, see [How to: Deploy a Data Processing Extension to Report Designer](deploying-a-data-processing-extension-to-report-designer.md).</span></span>  
  
3.  <span data-ttu-id="85a86-110">데이터 처리 확장 프로그램 코드를 별도의 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 창에 열어 둔 상태로 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 새 보고서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-110">Open a new Report Project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] while leaving your data processing extension code open in a separate window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
4.  <span data-ttu-id="85a86-111">데이터 처리 확장 프로그램 프로젝트를 포함하는 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 창으로 이동하고 코드에서 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-111">Navigate to the window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] that contains your data processing extension project and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="85a86-112">데이터 처리 확장 프로그램 프로젝트 창을 활성 상태로 두고 **디버그** 메뉴에서 **프로세스에 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-112">With the data processing extension project window still active, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="85a86-113">**프로세스에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-113">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="85a86-114">프로세스 목록에서 보고서 프로젝트에 해당하는 devenv.exe 프로세스를 선택하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-114">From the list of processes, select the devenv.exe process that corresponds to your Report Project and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="85a86-115">보고서 프로젝트의 **보고서 데이터** 탭을 사용하여 보고서 데이터 원본을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-115">Define your report data source using the **Report Data** tab of the Report Project.</span></span> <span data-ttu-id="85a86-116">대개 일반 쿼리 디자이너를 사용하여 사용자 지정 데이터 원본에 대해 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-116">You will most likely use the generic Query Designer to execute a query against your custom data source.</span></span> <span data-ttu-id="85a86-117">그러면 디버거가 호출되고 중단점에 해당하는 코드가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-117">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="85a86-118">F11 키를 사용하여 코드를 단계별로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="85a86-118">Step through your code using the F11 key.</span></span> <span data-ttu-id="85a86-119">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]를 사용하여 디버깅하는 방법은 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="85a86-119">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a86-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85a86-120">See Also</span></span>  
 <span data-ttu-id="85a86-121">[데이터 처리 확장 프로그램 배포](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="85a86-121">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="85a86-122">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="85a86-122">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="85a86-123">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="85a86-123">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="85a86-124">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="85a86-124">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
