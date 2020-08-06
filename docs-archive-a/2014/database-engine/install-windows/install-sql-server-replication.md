---
title: SQL Server 복제 설치 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ba941fda1d463e7bb4a26bd2fbb45d2a82ca27b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729760"
---
# <a name="install-sql-server-replication"></a><span data-ttu-id="18f5e-102">SQL Server 복제 설치</span><span class="sxs-lookup"><span data-stu-id="18f5e-102">Install SQL Server Replication</span></span>
  <span data-ttu-id="18f5e-103">복제 구성 요소는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사 또는 명령 프롬프트를 사용하여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18f5e-103">Replication components can be installed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or at a command prompt.</span></span> <span data-ttu-id="18f5e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 설치할 때나 기존 인스턴스를 수정할 때 복제를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18f5e-104">Install replication when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or when you modify an existing instance.</span></span>  
  
 <span data-ttu-id="18f5e-105">복제 구성 요소를 설치한 후에는 복제를 사용하기 전에 먼저 서버를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18f5e-105">After replication components are installed, you must configure the server before you can use replication.</span></span> <span data-ttu-id="18f5e-106">자세한 내용은 [온라인 설명서의](../../relational-databases/replication/configure-distribution.md) 배포 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18f5e-106">For more information, see [Configure Distribution](../../relational-databases/replication/configure-distribution.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="18f5e-107">기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 수정할 때 복제 구성 요소를 설치하는 경우 설치가 완료된 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 중지하고 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18f5e-107">If you install replication components when you modify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent after the installation is completed.</span></span> <span data-ttu-id="18f5e-108">이 동작을 수행하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 복제 에이전트 하위 시스템을 인식하며 작업 단계에서 복제 에이전트를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18f5e-108">This action helps ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent recognizes the replication agent subsystems and can call replication agents from job steps.</span></span>  
  
## <a name="installing-replication-by-using-setup"></a><span data-ttu-id="18f5e-109">설치 프로그램을 사용하여 복제 설치</span><span class="sxs-lookup"><span data-stu-id="18f5e-109">Installing Replication by Using Setup</span></span>  
 <span data-ttu-id="18f5e-110">**다음의 새 인스턴스를 설치할 때 복제를 설치하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="18f5e-110">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="18f5e-111">RMO(복제 관리 개체)를 비롯한 복제 구성 요소를 설치하려면 설치 마법사의 **기능 선택** 페이지에서 **SQL Server 복제** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="18f5e-111">To install replication components, including Replication Management Objects (RMO), select **SQL Server Replication** on the **Feature Selection** page of the Installation Wizard.</span></span>  
  
## <a name="installing-replication-from-the-command-prompt"></a><span data-ttu-id="18f5e-112">명령 프롬프트에서 복제 설치</span><span class="sxs-lookup"><span data-stu-id="18f5e-112">Installing Replication from the Command Prompt</span></span>  
 <span data-ttu-id="18f5e-113">**다음의 새 인스턴스를 설치할 때 복제를 설치하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="18f5e-113">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="18f5e-114">[명령 프롬프트에서 SQL Server 2014 설치를](install-sql-server-from-the-command-prompt.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="18f5e-114">See [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f5e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18f5e-115">See Also</span></span>  
 <span data-ttu-id="18f5e-116">[SQL Server 2014 설치](install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="18f5e-116">[Install SQL Server 2014](install-sql-server.md) </span></span>  
 <span data-ttu-id="18f5e-117">[명령 프롬프트에서 SQL Server 2014 설치](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="18f5e-117">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 [<span data-ttu-id="18f5e-118">SQL Server 2014 버전에서 지원하는 기능</span><span class="sxs-lookup"><span data-stu-id="18f5e-118">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
