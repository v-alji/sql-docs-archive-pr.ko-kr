---
title: 사용자 지정 로그 공급자의 사용자 인터페이스 개발 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c3ce6cf5ad744e307bbb049347047bf94fc5a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647163"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a><span data-ttu-id="02fb9-102">사용자 지정 로그 공급자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="02fb9-102">Developing a User Interface for a Custom Log Provider</span></span>
  <span data-ttu-id="02fb9-103">대부분의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 로그 공급자에는 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>를 구현하며 **SSIS 로그 구성** 대화 상자의 **구성** 텍스트 상자를 사용 가능한 연결 관리자의 필터링된 드롭다운 목록으로 바꾸는 사용자 지정 사용자 인터페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02fb9-103">Many [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] log providers have a custom user interface that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> and replaces the **Configuration** text box in the **Configure SSIS Logs** dialog box with a filtered dropdown list of available connection managers.</span></span> <span data-ttu-id="02fb9-104">그러나 사용자 지정 로그 공급자의 사용자 지정 사용자 인터페이스는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 구현되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="02fb9-104">However, custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
<span data-ttu-id="02fb9-105">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="02fb9-105">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="02fb9-106">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="02fb9-106">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="02fb9-107">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="02fb9-107">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="02fb9-108">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="02fb9-108">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02fb9-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02fb9-109">See Also</span></span>  
 <span data-ttu-id="02fb9-110">[사용자 지정 로그 공급자 만들기](creating-a-custom-log-provider.md) </span><span class="sxs-lookup"><span data-stu-id="02fb9-110">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) </span></span>  
 [<span data-ttu-id="02fb9-111">사용자 지정 로그 공급자 코딩</span><span class="sxs-lookup"><span data-stu-id="02fb9-111">Coding a Custom Log Provider</span></span>](coding-a-custom-log-provider.md)  
  
  
