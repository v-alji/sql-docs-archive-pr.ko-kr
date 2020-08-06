---
title: SqlErrorLogEvent 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 358b6906e422be2984f2ebdbde636ad0b8376993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649957"
---
# <a name="sqlerrorlogevent-class"></a><span data-ttu-id="2e622-102">SqlErrorLogEvent 클래스</span><span class="sxs-lookup"><span data-stu-id="2e622-102">SqlErrorLogEvent Class</span></span>
  <span data-ttu-id="2e622-103">지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 파일에서 이벤트를 보기 위한 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-103">Provides properties for viewing events in a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e622-104">구문</span><span class="sxs-lookup"><span data-stu-id="2e622-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="2e622-105">속성</span><span class="sxs-lookup"><span data-stu-id="2e622-105">Properties</span></span>  
 <span data-ttu-id="2e622-106">SQLErrorLogEvent 클래스는 다음 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-106">The SQLErrorLogEvent class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e622-107">FileName</span><span class="sxs-lookup"><span data-stu-id="2e622-107">FileName</span></span>|<span data-ttu-id="2e622-108">데이터 형식: `string`</span><span class="sxs-lookup"><span data-stu-id="2e622-108">Data type: `string`</span></span><br /><br /> <span data-ttu-id="2e622-109">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="2e622-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="2e622-110">오류 로그 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-110">The name of the error log file.</span></span>|  
|<span data-ttu-id="2e622-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="2e622-111">InstanceName</span></span>|<span data-ttu-id="2e622-112">데이터 형식: `string`</span><span class="sxs-lookup"><span data-stu-id="2e622-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="2e622-113">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="2e622-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="2e622-114">한정자: Key</span><span class="sxs-lookup"><span data-stu-id="2e622-114">Qualifiers: Key</span></span><br /><br /> <span data-ttu-id="2e622-115">로그 파일이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="2e622-116">LogDate</span><span class="sxs-lookup"><span data-stu-id="2e622-116">LogDate</span></span>|<span data-ttu-id="2e622-117">데이터 형식: `datetime`</span><span class="sxs-lookup"><span data-stu-id="2e622-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="2e622-118">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="2e622-118">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="2e622-119">한정자: Key</span><span class="sxs-lookup"><span data-stu-id="2e622-119">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="2e622-120">이벤트가 로그 파일에 기록된 날짜와 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-120">The date and time that the event was recorded in the log file.</span></span>|  
|<span data-ttu-id="2e622-121">메시지</span><span class="sxs-lookup"><span data-stu-id="2e622-121">Message</span></span>|<span data-ttu-id="2e622-122">데이터 형식: `string`</span><span class="sxs-lookup"><span data-stu-id="2e622-122">Data type: `string`</span></span><br /><br /> <span data-ttu-id="2e622-123">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="2e622-123">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="2e622-124">이벤트 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-124">The event message.</span></span>|  
|<span data-ttu-id="2e622-125">ProcessInfo</span><span class="sxs-lookup"><span data-stu-id="2e622-125">ProcessInfo</span></span>|<span data-ttu-id="2e622-126">데이터 형식: `string`</span><span class="sxs-lookup"><span data-stu-id="2e622-126">Data type: `string`</span></span><br /><br /> <span data-ttu-id="2e622-127">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="2e622-127">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="2e622-128">이벤트의 SPID(원본 서버 프로세스 ID)에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-128">Information about the source server process ID (SPID) for the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e622-129">설명</span><span class="sxs-lookup"><span data-stu-id="2e622-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e622-130">MOF</span><span class="sxs-lookup"><span data-stu-id="2e622-130">MOF</span></span>|<span data-ttu-id="2e622-131">Sqlmgmproviderxpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="2e622-131">Sqlmgmproviderxpsp2up.mof</span></span>|  
|<span data-ttu-id="2e622-132">DLL</span><span class="sxs-lookup"><span data-stu-id="2e622-132">DLL</span></span>|<span data-ttu-id="2e622-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="2e622-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="2e622-134">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="2e622-134">Namespace</span></span>|<span data-ttu-id="2e622-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="2e622-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2e622-136">예제</span><span class="sxs-lookup"><span data-stu-id="2e622-136">Example</span></span>  
 <span data-ttu-id="2e622-137">다음 예에서는 지정된 로그 파일에서 로깅된 모든 이벤트의 값을 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-137">The following example shows how to retrieve values for all logged events in a specified log file.</span></span> <span data-ttu-id="2e622-138">예제를 실행 하려면을 \<*Instance_Name*> ' Instance1 '과 같은의 인스턴스 이름으로 바꾸고, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ' File_Name '을 오류 로그 파일의 이름 (예: ' ')으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-138">To run the example, replace \<*Instance_Name*> with the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as 'Instance1', and replace 'File_Name' with the name of the error log file, such as 'ERRORLOG.1'.</span></span>  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a><span data-ttu-id="2e622-139">주석</span><span class="sxs-lookup"><span data-stu-id="2e622-139">Comments</span></span>  
 <span data-ttu-id="2e622-140">*InstanceName* 또는 *FileName* 이 WQL 문에 제공 되지 않은 경우 쿼리는 기본 인스턴스와 현재 로그 파일에 대 한 정보를 반환 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2e622-140">When *InstanceName* or *FileName* are not provided in the WQL statement, the query will return information for the default instance and the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span> <span data-ttu-id="2e622-141">예를 들어 다음 WQL 문은 기본 인스턴스(MSSQLSERVER)의 현재 로그 파일(ERRORLOG)에서 모든 로그 이벤트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-141">For example, the following WQL statement will return all log events from the current log file (ERRORLOG) on the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a><span data-ttu-id="2e622-142">보안</span><span class="sxs-lookup"><span data-stu-id="2e622-142">Security</span></span>  
 <span data-ttu-id="2e622-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]WMI를 통해 로그 파일에 연결 하려면 로컬 컴퓨터와 원격 컴퓨터 모두에 대 한 다음 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="2e622-144">**Root\Microsoft\SqlServer\ComputerManagement10** WMI 네임 스페이스에 대 한 읽기 액세스입니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="2e622-145">기본적으로 모든 사용자는 계정 사용 권한으로 읽기 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
-   <span data-ttu-id="2e622-146">오류 로그를 포함하는 폴더에 대한 읽기 권한.</span><span class="sxs-lookup"><span data-stu-id="2e622-146">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="2e622-147">기본적으로 오류 로그는 다음 경로에 있습니다. 여기서 \*는를 \<*Drive> 설치한 드라이브를 나타내고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<*InstanceName*> 는 인스턴스의 이름입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2e622-147">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="2e622-148">\*\* \<Drive> : Files\Microsoft SQL Server\MSSQL12\*\* **. \<InstanceName> \MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="2e622-148">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="2e622-149">방화벽을 통해 연결하는 경우 방화벽에 원격 대상 컴퓨터의 WMI에 대한 예외가 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e622-149">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="2e622-150">자세한 내용은 [Windows Vista부터 원격으로 WMI에 연결](https://go.microsoft.com/fwlink/?LinkId=178848)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2e622-150">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e622-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e622-151">See Also</span></span>  
 <span data-ttu-id="2e622-152">[SqlErrorLogFile 클래스](sqlerrorlogfile-class.md) </span><span class="sxs-lookup"><span data-stu-id="2e622-152">[SqlErrorLogFile Class](sqlerrorlogfile-class.md) </span></span>  
 [<span data-ttu-id="2e622-153">오프라인 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="2e622-153">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
