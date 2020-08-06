---
title: Integration Services 서비스에 대 한 사용 권한 부여 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e7ab0c2f482e5a0b1bfeaa06f38ec5a886420a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647130"
---
# <a name="grant-permissions-to-integration-services-service"></a><span data-ttu-id="792f6-102">Integration Services 서비스에 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="792f6-102">Grant Permissions to Integration Services Service</span></span>
  <span data-ttu-id="792f6-103">이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 설치하면 기본적으로 Users 그룹의 모든 사용자에게 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대한 액세스 권한이 부여되었지만</span><span class="sxs-lookup"><span data-stu-id="792f6-103">In previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], by default when you installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] all users in the Users group had access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="792f6-104">현재 릴리스의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 설치하면 사용자에게 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대한 액세스 권한이 부여되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-104">When you install the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], users do not have access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="792f6-105">이 서비스에는 기본적으로 보안이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-105">The service is secure by default.</span></span> <span data-ttu-id="792f6-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가 설치된 후 관리자가 서비스에 대한 액세스 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-106">After [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is installed, the administrator must grant access to the service.</span></span>  
  
### <a name="to-grant-access-to-the-integration-services-service"></a><span data-ttu-id="792f6-107">Integration Services 서비스에 대한 액세스 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="792f6-107">To grant access to the Integration Services service</span></span>  
  
1.  <span data-ttu-id="792f6-108">Dcomcnfg.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-108">Run Dcomcnfg.exe.</span></span> <span data-ttu-id="792f6-109">Dcomcnfg.exe는 레지스트리의 특정 설정을 수정하는 사용자 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-109">Dcomcnfg.exe provides a user interface for modifying certain settings in the registry.</span></span>  
  
2.  <span data-ttu-id="792f6-110">**구성 요소 서비스** 대화 상자에서 구성 요소 서비스 > 컴퓨터 > 내 컴퓨터 > DCOM 구성 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-110">In the **Component Services** dialog, expand the Component Services > Computers > My Computer > DCOM Config node.</span></span>  
  
3.  <span data-ttu-id="792f6-111">**Microsoft SQL Server Integration Services 12.0**을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-111">Right-click **Microsoft SQL Server Integration Services 12.0**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="792f6-112">**보안** 탭의 **시작 및 활성화 권한** 영역에서 **편집** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-112">On the **Security** tab, click **Edit** in the **Launch and Activation Permissions** area.</span></span>  
  
5.  <span data-ttu-id="792f6-113">사용자를 추가하고 적절한 권한을 할당한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-113">Add users and assign appropriate permissions, and then click Ok.</span></span>  
  
6.  <span data-ttu-id="792f6-114">액세스 권한에 대해 4-5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-114">Repeat steps 4 - 5 for Access Permissions.</span></span>  
  
7.  <span data-ttu-id="792f6-115">SQL Server Management Studio를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-115">Restart SQL Server Management Studio.</span></span>  
  
8.  <span data-ttu-id="792f6-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="792f6-116">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Service.</span></span>  
  
  
