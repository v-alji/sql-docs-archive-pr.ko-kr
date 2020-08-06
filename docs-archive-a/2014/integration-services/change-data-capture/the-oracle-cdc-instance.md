---
title: Oracle CDC 인스턴스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ed71e8c4-e013-4bf2-8b6c-1e833ff2a41d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2228872b5a190fd416dccaa8062dd79dbc1f7a79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651228"
---
# <a name="the-oracle-cdc-instance"></a><span data-ttu-id="bd5cd-102">Oracle CDC 인스턴스</span><span class="sxs-lookup"><span data-stu-id="bd5cd-102">The Oracle CDC Instance</span></span>
  <span data-ttu-id="bd5cd-103">Oracle CDC 인스턴스는 단일 Oracle 원본 데이터베이스에서 캡처된 변경 내용을 처리하기 위해 Oracle CDC Service에서 만든 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-103">The Oracle CDC Instance is a process created by the Oracle CDC Service to process changes captured from a single Oracle source database.</span></span> <span data-ttu-id="bd5cd-104">Oracle CDC 인스턴스는 **cdc.xdbcdc_config** 테이블에서 구성을 검색하고 **cdc.xdbcdc_state** 테이블에서 상태를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-104">The Oracle CDC Instance retrieves its configuration from the **cdc.xdbcdc_config** table and maintains its state in the **cdc.xdbcdc_state** table.</span></span> <span data-ttu-id="bd5cd-105">이러한 테이블은 Oracle CDC 인스턴스를 정의하는 CDC 데이터베이스의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-105">These tables are part of the CDC database, which defines the Oracle CDC Instance.</span></span> <span data-ttu-id="bd5cd-106">xdbcdc 데이터베이스 및 테이블에 대한 자세한 내용은 [The CDC Databases](the-oracle-cdc-service.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-106">For more information about the xdbcdc database and tables see [The CDC Databases](the-oracle-cdc-service.md).</span></span>  
  
 <span data-ttu-id="bd5cd-107">다음은 Oracle CDC 인스턴스에 의해 수행되는 태스크에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-107">The following describes the tasks carried out by the Oracle CDC instance:</span></span>  
  
-   <span data-ttu-id="bd5cd-108">**서비스 시작 확인 처리**: 시작할 때 CDC 인스턴스는 **xdbcdc_config** 테이블에서 구성을 로드하고 상태 확인을 수행하여 CDC 인스턴스 지속 상태가 일관되고 변경 처리를 시작할 수 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-108">**Handling service startup verification**: When started, the CDC instance loads its configuration from the **xdbcdc_config** table and performs a series of status verifications that ensure that the CDC instance persisted state is consistent and that it can start processing changes.</span></span>  
  
-   <span data-ttu-id="bd5cd-109">**변경 캡처 준비**: 확인에 통과하면 Oracle CDC 인스턴스는 현재 정의된 모든 캡처 인스턴스를 검색하고 변경 캡처에 필요한 Oracle LogMiner 쿼리와 다른 지원 구조를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-109">**Preparing for change capture**: When the verification passes successfully, the Oracle CDC Instance scans all of the capture instances currently defined and prepares the Oracle LogMiner queries and other support structures required for change capture.</span></span> <span data-ttu-id="bd5cd-110">또한 Oracle 인스턴스는 Oracle CDC 인스턴스를 마지막으로 실행할 때 저장된 내부 캡처 상태를 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-110">In addition, the Oracle instance re-loads the internal capture state that was saved the last time the Oracle CDC Instance run.</span></span>  
  
-   <span data-ttu-id="bd5cd-111">**Oracle에서 변경 내용 캡처**: Oracle CDC 인스턴스는 Oracle LogMiner 기능을 사용하여 Oracle에서 변경 내용을 풀링하여 트랜잭션 커밋에 따라 정렬한 다음 트랜잭션 시간을 변경하여 CDC 데이터베이스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 변경 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-111">**Capturing changes from Oracle**: The Oracle CDC Instance pools changes from Oracle by means of the Oracle LogMiner facility, orders them in according to transaction commit, and then changes the time in a transaction and writes them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables in the CDC database.</span></span>  
  
-   <span data-ttu-id="bd5cd-112">**서비스 종료 처리**: Oracle CDC 인스턴스의 수명 주기는 Oracle CDC Service에 의해 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-112">**Handling service shutdown**: The life cycle of the Oracle CDC Instance is managed by the Oracle CDC Service.</span></span> <span data-ttu-id="bd5cd-113">Oracle CDC 인스턴스는 종료하도록 요청되면 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-113">When the Oracle CDC Instance is requested to shut down, it performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="bd5cd-114">Oracle 트랜잭션 로그 읽기를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-114">Stops reading from the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="bd5cd-115">CDC 데이터베이스에 완료된 Oracle 트랜잭션 쓰기를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-115">Stops writing completed Oracle transactions to the CDC database.</span></span>  
  
    -   <span data-ttu-id="bd5cd-116">필요한 경우 현재 트랜잭션이 CDC 데이터베이스에 기록될 때까지 30초까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-116">Waits for up to 30 seconds (if necessary) until the current transaction finishes writing to the CDC database.</span></span> <span data-ttu-id="bd5cd-117">30초가 초과되면 쓰기가 취소되고 트랜잭션이 롤백됩니다(CDC 인스턴스를 다시 시작하면 다시 시도됨).</span><span class="sxs-lookup"><span data-stu-id="bd5cd-117">If more than 30 seconds pass, the writing is cancelled and transaction is rolled back (to be retried when the CDC instance is restarted).</span></span>  
  
    -   <span data-ttu-id="bd5cd-118">별도의 스레드에서 최대 30초 동안 메모리에 캐시된 레코드를 준비된 트랜잭션 테이블에 최대한 많이 기록한 다음(오래된 트랜잭션부터 순서대로) **xdbcdc_state** 테이블을 업데이트하고 모든 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-118">In a separate thread, writes as many memory-cached records as possible to the staged transactions table for up to 30 seconds (from the oldest transaction to the newest), then updates the **xdbcdc_state** table and commits all the changes.</span></span>  
  
-   <span data-ttu-id="bd5cd-119">**구성 변경 처리**: Oracle CDC 인스턴스는 **cdc.xdbcdc_config** 테이블에서 새 버전을 검색하거나 CDC Service를 통해 구성 변경에 대한 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-119">**Handling configuration changes**: The Oracle CDC Instance is notified about configuration changes either from the CDC Service or by detecting a new version in the **cdc.xdbcdc_config** table.</span></span> <span data-ttu-id="bd5cd-120">대부분의 변경(예: 캡처 인스턴스 추가 또는 제거)은 Oracle CDC 인스턴스를 다시 시작할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-120">Most changes do not require the restart of the Oracle CDC Instance (for example, adding or removing capture instances).</span></span> <span data-ttu-id="bd5cd-121">일부 변경(예: Oracle 연결 문자열 또는 액세스 자격 증명 변경)은 CDC 인스턴스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-121">However, some changes, such as changing the Oracle connection string or access credentials do require the restart of the CDC Instance.</span></span>  
  
-   <span data-ttu-id="bd5cd-122">**복원 처리**: Oracle CDC 인스턴스가 시작되면 내부 상태가 **xdbcdc_state** 및 **xdbcdc_staged_transactions** 테이블에서 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-122">**Handling recovery**: When an Oracle CDC Instance starts its internal state is restored from the **xdbcdc_state** and the **xdbcdc_staged_transactions** tables.</span></span> <span data-ttu-id="bd5cd-123">상태가 복원되면 CDC 인스턴스가 평소와 같이 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd5cd-123">Once the state is restored, the CDC instance proceeds as usual.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5cd-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd5cd-124">See Also</span></span>  
 [<span data-ttu-id="bd5cd-125">오류 처리</span><span class="sxs-lookup"><span data-stu-id="bd5cd-125">Error Handling</span></span>](error-handling.md)  
  
  
