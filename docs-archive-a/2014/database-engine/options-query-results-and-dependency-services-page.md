---
title: 옵션 (쿼리 결과 및 종속성 서비스 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 356714ee933fb40eda7038f4088309b6187f3ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659643"
---
# <a name="options-query-results-and-dependency-services-page"></a><span data-ttu-id="9cf1b-102">옵션(쿼리 결과 및 종속성 서비스 페이지)</span><span class="sxs-lookup"><span data-stu-id="9cf1b-102">Options (Query Results and Dependency Services Page)</span></span>
  <span data-ttu-id="9cf1b-103">이 페이지를 사용하여 종속성 서비스를 위해 연결할 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-103">Use this page to specify the server to connect for Dependency Services.</span></span> <span data-ttu-id="9cf1b-104">종속성 서비스를 사용하면 서로 다른 서버에 저장된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 및 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체 간의 종속성에 대한 정보를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-104">Dependency Services enables you to extract information about dependencies between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects stored on different servers.</span></span> <span data-ttu-id="9cf1b-105">에서 **개체 종속성** 대화 상자를 사용 하 여 개체 종속성을 볼 수 있습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9cf1b-105">You view object dependencies by using the **Object Dependencies** dialog box in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="9cf1b-106">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="9cf1b-106">**What do you want to do?**</span></span>  
  
1.  [<span data-ttu-id="9cf1b-107">옵션(쿼리 결과/종속성 서비스 페이지) 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="9cf1b-107">Open the Options (Query Results/Dependency Services Page) Dialog Box</span></span>](#open_dialog)  
  
2.  [<span data-ttu-id="9cf1b-108">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="9cf1b-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a><span data-ttu-id="9cf1b-109">옵션 (쿼리 결과/종속성 서비스 페이지) 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="9cf1b-109">Open the Options (Query Results/Dependency Services Page) Dialog Box</span></span>  
  
1.  <span data-ttu-id="9cf1b-110">의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] **도구** 메뉴에서 **옵션** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-110">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="9cf1b-111">**쿼리 결과**를 확장하고 **종속성 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-111">Expand **Query Results**, and then click **Dependency Services**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="9cf1b-112">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="9cf1b-112">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="9cf1b-113">옵션</span><span class="sxs-lookup"><span data-stu-id="9cf1b-113">Options</span></span>  
 <span data-ttu-id="9cf1b-114">**종속성 서비스 서버**</span><span class="sxs-lookup"><span data-stu-id="9cf1b-114">**Dependency Services server**</span></span>  
 <span data-ttu-id="9cf1b-115">종속성 서비스가 설치된 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-115">Specify the server that Dependency Services is installed on.</span></span>  
  
 <span data-ttu-id="9cf1b-116">**인증**</span><span class="sxs-lookup"><span data-stu-id="9cf1b-116">**Authentication**</span></span>  
 <span data-ttu-id="9cf1b-117">Microsoft Windows 사용자 계정을 사용하여 로그온하려면 Windows 인증을 선택하고, 그렇지 않으면 SQL Server 인증을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-117">Select Windows Authentication to log on using a Microsoft Windows user account, or select SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="9cf1b-118">사용자가 트러스트되지 않은 연결에서 지정한 로그인 이름과 암호를 사용하여 연결하면 SQL Server에서는 SQL Server 로그인 계정이 설정되었는지 여부와 지정한 암호가 이전에 기록한 암호와 일치하는지 여부를 확인하여 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-118">When a user connects with a specified login name and password from a non-trusted connection, SQL Server performs the authentication by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="9cf1b-119">SQL Server에서 로그인 계정을 찾을 수 없으면 인증이 실패하고 사용자에게 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-119">If SQL Server cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="9cf1b-120">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="9cf1b-120">**User name**</span></span>  
 <span data-ttu-id="9cf1b-121">SQL Server 인증을 사용하는 경우 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-121">If using SQL Server Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="9cf1b-122">**암호**</span><span class="sxs-lookup"><span data-stu-id="9cf1b-122">**Password**</span></span>  
 <span data-ttu-id="9cf1b-123">SQL Server 인증을 사용하는 경우 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-123">If using SQL Server Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="9cf1b-124">**Test**</span><span class="sxs-lookup"><span data-stu-id="9cf1b-124">**Test**</span></span>  
 <span data-ttu-id="9cf1b-125">연결을 테스트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cf1b-125">Click to test the connection.</span></span>