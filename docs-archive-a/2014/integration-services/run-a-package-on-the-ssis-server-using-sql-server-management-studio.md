---
title: SQL Server Management Studio |를 사용 하 여 SSIS 서버에서 패키지 실행 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d17009988dea54621d4fd7ef542cf452bfe95c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729559"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a><span data-ttu-id="5181a-102">SQL Server Management Studio를 사용하여 SSIS 서버에서 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="5181a-102">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>
  <span data-ttu-id="5181a-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 프로젝트를 배포한 후에는 서버에서 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-103">After you deploy your project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you can run the package on the server.</span></span>  
  
 <span data-ttu-id="5181a-104">작업 보고서를 사용하여 서버에서 실행되었거나 현재 실행 중인 패키지에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-104">You can use operations reports to view information about packages that have run, or are currently running, on the server.</span></span> <span data-ttu-id="5181a-105">자세한 내용은 [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5181a-105">For more information, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a><span data-ttu-id="5181a-106">SQL Server Management Studio를 사용하여 서버에서 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="5181a-106">To run a package on the server using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="5181a-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 열고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 카탈로그가 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-107">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
2.  <span data-ttu-id="5181a-108">개체 탐색기에서 **Integration Services 카탈로그** 노드와 **SSISDB** 노드를 차례로 확장하고, 배포한 프로젝트에 포함된 패키지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-108">In Object Explorer, expand the **Integration Services Catalogs** node, expand the **SSISDB** node, and navigate to the package contained in the project you deployed.</span></span>  
  
3.  <span data-ttu-id="5181a-109">패키지 이름을 마우스 오른쪽 단추로 클릭하고 **실행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-109">Right-click the package name and select **Execute**.</span></span>  
  
4.  <span data-ttu-id="5181a-110">**패키지 실행**대화 상자의 **매개 변수**, **연결 관리자** 및 **고급** 탭의 설정을 사용하여 패키지 실행을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-110">Configure the package execution by using the settings on the **Parameters**, **Connection Managers**, and **Advanced** tabs in the **Execute Package** dialog box.</span></span>  
  
5.  <span data-ttu-id="5181a-111">**확인** 을 클릭하여 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-111">Click **OK** to run the package.</span></span>  
  
     <span data-ttu-id="5181a-112">또는</span><span class="sxs-lookup"><span data-stu-id="5181a-112">-or-</span></span>  
  
     <span data-ttu-id="5181a-113">저장 프로시저를 사용하여 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-113">Use stored procedures to run the package.</span></span> <span data-ttu-id="5181a-114">**스크립트** 를 클릭하여 실행 인스턴스를 만들고 실행 인스턴스를 시작하는 Transact-SQL 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-114">Click **Script** to generate the Transact-SQL statement that creates an instance of the execution and starts an instance of the execution.</span></span> <span data-ttu-id="5181a-115">문에는 catalog.create_execution, catalog.set_execution_parameter_value에 대한 호출과 catalog.start_execution 저장 프로시저가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5181a-115">The statement includes a call to the catalog.create_execution, catalog.set_execution_parameter_value, and catalog.start_execution stored procedures.</span></span> <span data-ttu-id="5181a-116">이러한 저장 프로시저에 대한 자세한 내용은 [catalog.create_execution&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) 및 [catalog.start_execution&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5181a-116">For more information about these stored procedures, see [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database), and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
  
