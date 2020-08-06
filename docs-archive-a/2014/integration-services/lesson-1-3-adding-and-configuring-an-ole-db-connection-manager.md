---
title: '3단계: OLE DB 연결 관리자 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bc4c885ce6c39c72031dd3b528a769cd47ac8f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651139"
---
# <a name="step-3-adding-and-configuring-an-ole-db-connection-manager"></a><span data-ttu-id="bc516-102">3단계: OLE DB 연결 관리자 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bc516-102">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>
  <span data-ttu-id="bc516-103">데이터 원본에 연결하기 위해 플랫 파일 연결 관리자를 추가한 후에는 OLE DB 연결 관리자를 추가하여 대상에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-103">After you have added a Flat File connection manager to connect to the data source, the next task is to add an OLE DB connection manager to connect to the destination.</span></span> <span data-ttu-id="bc516-104">OLE DB 연결 관리자를 사용하면 패키지가 OLE DB 호환 데이터 원본에서 데이터를 추출하거나 데이터를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-104">An OLE DB connection manager enables a package to extract data from or load data into any OLE DB-compliant data source.</span></span> <span data-ttu-id="bc516-105">OLE DB 연결 관리자를 사용하여 서버, 인증 방법 및 연결의 기본 데이터베이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-105">Using the OLE DB Connection manager, you can specify the server, the authentication method, and the default database for the connection.</span></span>  
  
 <span data-ttu-id="bc516-106">이 단원에서는 Windows 인증을 사용하여 **AdventureWorksDB2012**의 로컬 인스턴스에 연결하는 OLE DB 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-106">In this lesson, you will create an OLE DB connection manager that uses Windows Authentication to connect to the local instance of **AdventureWorksDB2012**.</span></span> <span data-ttu-id="bc516-107">여기서 만든 OLE DB 연결 관리자는 이 자습서의 뒷부분에서 만들 다른 구성 요소(예: 조회 변환 및 OLE DB 대상)도 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-107">The OLE DB connection manager that you create will also be referenced by other components that you will create later in this tutorial, such as the Lookup transformation and the OLE DB destination.</span></span>  
  
### <a name="to-add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a><span data-ttu-id="bc516-108">OLE DB 연결 관리자를 SSIS 패키지에 추가하고 구성하려면</span><span class="sxs-lookup"><span data-stu-id="bc516-108">To add and configure an OLE DB Connection Manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="bc516-109">**연결 관리자** 영역의 아무 곳이나 마우스 오른쪽 단추로 클릭한 다음 **새 OLE DB 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-109">Right-click anywhere in the **Connection Managers** area, and then click **New OLE DB Connection**.</span></span>  
  
2.  <span data-ttu-id="bc516-110">**OLE DB 연결 관리자 구성** 대화 상자에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-110">In the **Configure OLE DB Connection Manager** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="bc516-111">**서버 이름**에 **localhost**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-111">For **Server name**, enter **localhost**.</span></span>  
  
     <span data-ttu-id="bc516-112">서버 이름으로 localhost를 지정하면 연결 관리자는 로컬 컴퓨터에 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 기본 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-112">When you specify localhost as the server name, the connection manager connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="bc516-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 원격 인스턴스를 사용하려면 localhost 대신 연결하려는 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-113">To use a remote instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], replace localhost with the name of the server to which you want to connect.</span></span>  
  
4.  <span data-ttu-id="bc516-114">**서버에 로그온** 그룹에서 **Windows 인증 사용** 을 선택했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-114">In the **Log on to the server** group, verify that **Use Windows Authentication** is selected.</span></span>  
  
5.  <span data-ttu-id="bc516-115">**데이터베이스에 연결** 그룹의 **데이터베이스 이름 선택 또는 입력** 상자에서를 입력 하거나 선택 `AdventureWorksDW2012` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-115">In the **Connect to a database** group, in the **Select or enter a database name** box, type or select `AdventureWorksDW2012`.</span></span>  
  
6.  <span data-ttu-id="bc516-116">**연결 테스트** 를 클릭하여 지정한 연결 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-116">Click **Test Connection** to verify that the connection settings you have specified are valid.</span></span>  
  
7.  <span data-ttu-id="bc516-117">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-117">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="bc516-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="bc516-119">**OLE DB 연결 관리자 구성** 대화 상자의 **데이터 연결** 창에서 **localhost.AdventureWorksDW2012** 를 선택했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-119">In the **Data Connections** pane of the **Configure OLE DB Connection Manager** dialog box, verify that **localhost.AdventureWorksDW2012** is selected.</span></span>  
  
10. <span data-ttu-id="bc516-120">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc516-120">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bc516-121">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="bc516-121">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bc516-122">4단계: 패키지에 Data Flow Task 추가</span><span class="sxs-lookup"><span data-stu-id="bc516-122">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc516-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc516-123">See Also</span></span>  
 [<span data-ttu-id="bc516-124">OLE DB 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="bc516-124">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
