---
title: 패키지 역할 대화 상자 UI 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 389b29ddee5674af7ecd106f4f82d61bbb3a0f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734347"
---
# <a name="package-roles-dialog-box-ui-reference"></a><span data-ttu-id="c387f-102">패키지 역할 대화 상자 UI 참조</span><span class="sxs-lookup"><span data-stu-id="c387f-102">Package Roles Dialog Box UI Reference</span></span>
  <span data-ttu-id="c387f-103">**에서 사용할 수 있는** 패키지 역할 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]대화 상자를 통해 패키지에 대한 읽기 권한이 있는 데이터베이스 수준 역할 및 패키지에 대한 쓰기 권한이 있는 데이터베이스 수준 역할을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-103">Use the **Package Roles** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to specify the database-level roles that have read access to the package and the database-level roles that have write access to the package.</span></span> <span data-ttu-id="c387f-104">데이터베이스 수준 역할은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** 데이터베이스에 저장된 패키지에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-104">Database-level roles apply only to packages that are stored in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** database.</span></span>  
  
 <span data-ttu-id="c387f-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 데이터베이스 수준 역할과 해당 사용 권한에 대한 자세한 내용은 [Integration Services 역할&#40;SSIS 서비스&#41;](security/integration-services-roles-ssis-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c387f-105">To learn more about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] database-level roles and their permissions, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>  
  
 <span data-ttu-id="c387f-106">대화 상자에 나열된 역할은 **msdb** 시스템 데이터베이스의 현재 데이터베이스 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-106">The roles listed in the dialog box are the current database roles of the **msdb** system database.</span></span> <span data-ttu-id="c387f-107">역할을 선택하지 않으면 기본 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 역할이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-107">If no roles are selected, the default [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] roles apply.</span></span> <span data-ttu-id="c387f-108">기본적으로 읽기 역할에는 **db_ssisadmin**, **db_ssisoperator**및 패키지를 만든 사용자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-108">By default, the reader role includes **db_ssisadmin**, **db_ssisoperator**, and the user who created the package.</span></span> <span data-ttu-id="c387f-109">이러한 역할 중 하나의 멤버이거나 패키지를 만든 사용자는 패키지를 열거, 확인, 내보내기 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-109">A user who is a member of one of these roles or created the packages can enumerate, view, export, and run packages.</span></span> <span data-ttu-id="c387f-110">기본적으로 쓰기 역할에는 **db_ssisadmin** 과 패키지를 만든 사용자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-110">By default, the writer role includes **db_ssisadmin** and the user who created the package.</span></span> <span data-ttu-id="c387f-111">이 역할의 멤버인 사용자와 패키지를 만든 사용자는 패키지를 가져오거나 삭제 및 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-111">A user who is a member of this role and the user who created the packages can import, delete, and change packages.</span></span>  
  
 <span data-ttu-id="c387f-112">**sysssispackages** 테이블의 **ownersid** 열은 패키지를 만든 사용자의 고유 보안 식별자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-112">The **ownersid** column in the **sysssispackages** table lists the unique security identifier of the user who created the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c387f-113">옵션</span><span class="sxs-lookup"><span data-stu-id="c387f-113">Options</span></span>  
 <span data-ttu-id="c387f-114">**패키지 이름**</span><span class="sxs-lookup"><span data-stu-id="c387f-114">**Package Name**</span></span>  
 <span data-ttu-id="c387f-115">패키지의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-115">Specify the name of the package.</span></span>  
  
 <span data-ttu-id="c387f-116">**읽기 권한자 역할**</span><span class="sxs-lookup"><span data-stu-id="c387f-116">**Reader Role**</span></span>  
 <span data-ttu-id="c387f-117">목록에서 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-117">Select a role in the list.</span></span>  
  
 <span data-ttu-id="c387f-118">**쓰기 역할**</span><span class="sxs-lookup"><span data-stu-id="c387f-118">**Writer Role**</span></span>  
 <span data-ttu-id="c387f-119">목록에서 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c387f-119">Select a role in the list</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c387f-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c387f-120">See Also</span></span>  
 <span data-ttu-id="c387f-121">[데이터베이스 수준 역할](../relational-databases/security/authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="c387f-121">[Database-Level Roles](../relational-databases/security/authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="c387f-122">보안 개요&#40;Integration Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c387f-122">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
