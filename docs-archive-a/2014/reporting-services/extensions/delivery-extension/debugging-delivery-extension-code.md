---
title: 배달 확장 프로그램 코드 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb80ac97f5c0e346b208784f1fa5b857ff93ef57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741563"
---
# <a name="debugging-delivery-extension-code"></a><span data-ttu-id="25c53-102">배달 확장 프로그램 코드 디버깅</span><span class="sxs-lookup"><span data-stu-id="25c53-102">Debugging Delivery Extension Code</span></span>
  <span data-ttu-id="25c53-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]에서는 배달 확장 프로그램 코드를 분석하여 오류를 찾는 데 유용한 디버깅 도구를 다수 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your delivery extension code and locate errors in it.</span></span> <span data-ttu-id="25c53-104">작업하기 가장 좋은 도구는 수행하려는 작업에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="25c53-105">이 예에서는 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-delivery-extension-code"></a><span data-ttu-id="25c53-106">배달 확장 프로그램 코드를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="25c53-106">To debug your delivery extension code</span></span>  
  
1.  <span data-ttu-id="25c53-107">[!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]를 시작하고 배달 확장 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] and open your delivery extension project.</span></span>  
  
2.  <span data-ttu-id="25c53-108">프로젝트를 빌드하고 배달 확장 프로그램 어셈블리 및 해당하는 .pdb 파일을 보고서 서버 및 보고서 관리자에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-108">Build the project and deploy your delivery extension assembly and the accompanying .pdb file to the report server and Report Manager.</span></span> <span data-ttu-id="25c53-109">배포에 대한 자세한 내용은 [배달 확장 프로그램 배포](deploying-a-delivery-extension.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25c53-109">For more information about deployment, see [Deploying a Delivery Extension](deploying-a-delivery-extension.md).</span></span>  
  
3.  <span data-ttu-id="25c53-110">구독 사용자 인터페이스를 작성하여 보고서 관리자를 확장한 경우에는 배달 확장 프로그램 코드가 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 열려 있는 상태에서 Internet Explorer를 열고 보고서 관리자로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-110">If you have written a subscription user interface to extend Report Manager, open Internet Explorer and navigate to Report Manager while leaving your delivery extension code open in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="25c53-111">보고서 관리자에 대해 배포된 구독 사용자 인터페이스가 없는 경우에는 SOAP API를 사용하여 배달 확장 프로그램을 호출하는 위치인 클라이언트 애플리케이션을 열면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-111">If you do not have a subscription user interface deployed for Report Manager, simply open the client application from which you call your delivery extension using the SOAP API.</span></span>  
  
4.  <span data-ttu-id="25c53-112">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 및 배달 확장 프로그램 프로젝트로 이동하고 코드에서 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-112">Navigate to [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and your delivery extension project, and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="25c53-113">배달 확장 프로젝트를 활성 창 상태로 두고 **디버그** 메뉴에서 **프로세스에 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-113">With the delivery extension project still the active window, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="25c53-114">**프로세스에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-114">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="25c53-115">프로세스 목록에서 aspnet_wp.exe 프로세스(애플리케이션을 IIS 6.0에서 배포할 경우 w3wp.exe)를 선택하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-115">From the list of processes, select the aspnet_wp.exe process (or w3wp.exe if your application is deployed on IIS 6.0), and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="25c53-116">배달 확장 프로그램을 사용하여 새 구독을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-116">Define a new subscription using your delivery extension.</span></span> <span data-ttu-id="25c53-117">대부분의 경우 보고서 관리자 또는 SOAP API를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-117">You will most likely use Report Manager or the SOAP API.</span></span> <span data-ttu-id="25c53-118">그러면 디버거가 호출되고 중단점에 해당하는 코드가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-118">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="25c53-119">**F11** 키를 사용하여 코드를 단계별로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="25c53-119">Step through your code using the **F11** key.</span></span> <span data-ttu-id="25c53-120">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]를 사용하여 디버깅하는 방법은 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="25c53-120">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c53-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25c53-121">See Also</span></span>  
 <span data-ttu-id="25c53-122">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="25c53-122">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="25c53-123">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="25c53-123">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
