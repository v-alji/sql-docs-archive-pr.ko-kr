---
title: Reporting Services SharePoint 모드 인증 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3b1316a1a49726ab0754f39160125425fec116d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737534"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a><span data-ttu-id="d4bc4-102">Reporting Services SharePoint 모드 인증</span><span class="sxs-lookup"><span data-stu-id="d4bc4-102">Reporting Services SharePoint Mode Authentication</span></span>
  <span data-ttu-id="d4bc4-103">\*\*\*\*[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 페이지를 사용하여 현재 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에서 사용되는 서비스 계정의 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-103">Use the **Reporting Services SharePoint Mode Authentication** page of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify the credentials of the service account that is used in the current [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="d4bc4-104">자격 증명은 새 SharePoint 애플리케이션 풀을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-104">The credentials will be used to create a new SharePoint application pool.</span></span> <span data-ttu-id="d4bc4-105">또한 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 서비스 애플리케이션이 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-105">Also, one new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service application will be created.</span></span> <span data-ttu-id="d4bc4-106">서비스 애플리케이션 이름에는 이전 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-106">The service application name will contain the name of the previous [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4bc4-107">옵션</span><span class="sxs-lookup"><span data-stu-id="d4bc4-107">Options</span></span>  
  
-   <span data-ttu-id="d4bc4-108">**SSRS 애플리케이션 풀 계정 이름:** 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-108">The **SSRS Application Pool Account Name:** option is read only.</span></span> <span data-ttu-id="d4bc4-109">값은 업그레이드할 기존 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치의 현재 값으로 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-109">The value is automatically populated with the current value from the existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that you are upgrading.</span></span>  
  
-   <span data-ttu-id="d4bc4-110">애플리케이션 풀 계정에 암호가 필요 하지 않은 경우 **SSRS 애플리케이션 풀 계정 암호:** 옵션이 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-110">The **SSRS Application Pool Account Password:** option will be disabled if the application pool account does not require a password.</span></span> <span data-ttu-id="d4bc4-111">예를 들면 "NT Authority\NetworkService"입니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-111">For example, "NT Authority\NetworkService".</span></span> <span data-ttu-id="d4bc4-112">애플리케이션 풀 계정에 암호가 필요하지 않은 경우 올바른 암호를 입력할 때까지 업그레이드를 계속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4bc4-112">If the application pool account does require a password, you cannot continue with upgrade until you type the correct password.</span></span>  
  
 <span data-ttu-id="d4bc4-113">자세한 내용은 [업그레이드 및 마이그레이션 Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) ()을 참조 하세요 https://go.microsoft.com/fwlink/?LinkID=245628) .</span><span class="sxs-lookup"><span data-stu-id="d4bc4-113">For more information, see [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bc4-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4bc4-114">See Also</span></span>  
 [<span data-ttu-id="d4bc4-115">Reporting Services 업그레이드 및 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="d4bc4-115">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
