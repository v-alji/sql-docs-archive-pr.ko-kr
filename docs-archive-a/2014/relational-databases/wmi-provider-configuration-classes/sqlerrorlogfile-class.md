---
title: SqlErrorLogFile 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d73f97ebddd7a1d18c73a2cbce7fe79dafc17a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729219"
---
# <a name="sqlerrorlogfile-class"></a><span data-ttu-id="de5c6-102">SqlErrorLogFile 클래스</span><span class="sxs-lookup"><span data-stu-id="de5c6-102">SqlErrorLogFile Class</span></span>
  <span data-ttu-id="de5c6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 파일에 대한 정보를 보기 위한 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-103">Provides properties for viewing information about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de5c6-104">구문</span><span class="sxs-lookup"><span data-stu-id="de5c6-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="de5c6-105">속성</span><span class="sxs-lookup"><span data-stu-id="de5c6-105">Properties</span></span>  
 <span data-ttu-id="de5c6-106">SQLErrorLogFile 클래스는 다음 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-106">The SQLErrorLogFile class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de5c6-107">ArchiveNumber</span><span class="sxs-lookup"><span data-stu-id="de5c6-107">ArchiveNumber</span></span>|<span data-ttu-id="de5c6-108">데이터 형식: `uint32`</span><span class="sxs-lookup"><span data-stu-id="de5c6-108">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="de5c6-109">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="de5c6-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="de5c6-110">로그 파일에 대한 보관 파일 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-110">The archive number for the log file.</span></span>|  
|<span data-ttu-id="de5c6-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="de5c6-111">InstanceName</span></span>|<span data-ttu-id="de5c6-112">데이터 형식: `string`</span><span class="sxs-lookup"><span data-stu-id="de5c6-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="de5c6-113">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="de5c6-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="de5c6-114">한정자: Key</span><span class="sxs-lookup"><span data-stu-id="de5c6-114">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="de5c6-115">로그 파일이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="de5c6-116">LastModified</span><span class="sxs-lookup"><span data-stu-id="de5c6-116">LastModified</span></span>|<span data-ttu-id="de5c6-117">데이터 형식: `datetime`</span><span class="sxs-lookup"><span data-stu-id="de5c6-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="de5c6-118">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="de5c6-118">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="de5c6-119">로그 파일이 마지막으로 수정된 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-119">The date that the log file was last modified.</span></span>|  
|<span data-ttu-id="de5c6-120">LogFileSize</span><span class="sxs-lookup"><span data-stu-id="de5c6-120">LogFileSize</span></span>|<span data-ttu-id="de5c6-121">데이터 형식: `uint32`</span><span class="sxs-lookup"><span data-stu-id="de5c6-121">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="de5c6-122">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="de5c6-122">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="de5c6-123">로그 파일의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-123">The log file size, in bytes.</span></span>|  
|<span data-ttu-id="de5c6-124">Name</span><span class="sxs-lookup"><span data-stu-id="de5c6-124">Name</span></span>|<span data-ttu-id="de5c6-125">데이터 형식: `string`</span><span class="sxs-lookup"><span data-stu-id="de5c6-125">Data type: `string`</span></span><br /><br /> <span data-ttu-id="de5c6-126">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="de5c6-126">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="de5c6-127">한정자: Key</span><span class="sxs-lookup"><span data-stu-id="de5c6-127">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="de5c6-128">로그 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-128">The name of the log file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de5c6-129">설명</span><span class="sxs-lookup"><span data-stu-id="de5c6-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de5c6-130">MOF</span><span class="sxs-lookup"><span data-stu-id="de5c6-130">MOF</span></span>|<span data-ttu-id="de5c6-131">Sqlmgmprovider xpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="de5c6-131">Sqlmgmprovider xpsp2up.mof</span></span>|  
|<span data-ttu-id="de5c6-132">DLL</span><span class="sxs-lookup"><span data-stu-id="de5c6-132">DLL</span></span>|<span data-ttu-id="de5c6-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="de5c6-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="de5c6-134">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="de5c6-134">Namespace</span></span>|<span data-ttu-id="de5c6-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="de5c6-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de5c6-136">예제</span><span class="sxs-lookup"><span data-stu-id="de5c6-136">Example</span></span>  
 <span data-ttu-id="de5c6-137">다음 예에서는 지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 파일에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-137">The following example retrieves information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de5c6-138">예제를 실행 하려면를 \<*Instance_Name*> 인스턴스 이름으로 바꿉니다 (예: ' Instance1 ').</span><span class="sxs-lookup"><span data-stu-id="de5c6-138">To run the example, replace \<*Instance_Name*> with the name of the instance, for example, 'Instance1'.</span></span>  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a><span data-ttu-id="de5c6-139">주석</span><span class="sxs-lookup"><span data-stu-id="de5c6-139">Comments</span></span>  
 <span data-ttu-id="de5c6-140">*InstanceName* 이 WQL 문에 제공 되지 않은 경우 쿼리는 기본 인스턴스에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-140">When *InstanceName* is not provided in the WQL statement, the query will return information for the default instance.</span></span> <span data-ttu-id="de5c6-141">예를 들어 다음 WQL 문은 기본 인스턴스(MSSQLSERVER)에서 모든 로그 파일에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-141">For example, the following WQL statement will return information about all log files from the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a><span data-ttu-id="de5c6-142">보안</span><span class="sxs-lookup"><span data-stu-id="de5c6-142">Security</span></span>  
 <span data-ttu-id="de5c6-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]WMI를 통해 로그 파일에 연결 하려면 로컬 컴퓨터와 원격 컴퓨터 모두에 대 한 다음 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="de5c6-144">**Root\Microsoft\SqlServer\ComputerManagement10** WMI 네임 스페이스에 대 한 읽기 액세스입니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="de5c6-145">기본적으로 모든 사용자는 계정 사용 권한으로 읽기 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de5c6-146">WMI 사용 권한을 확인 하는 방법에 대 한 자세한 내용은 [오프 라인 로그 파일 보기](../logs/view-offline-log-files.md)항목의 보안 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de5c6-146">For information about how to verify WMI permissions, see the Security section of the topic [View Offline Log Files](../logs/view-offline-log-files.md).</span></span>  
  
-   <span data-ttu-id="de5c6-147">오류 로그를 포함하는 폴더에 대한 읽기 권한.</span><span class="sxs-lookup"><span data-stu-id="de5c6-147">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="de5c6-148">기본적으로 오류 로그는 다음 경로에 있습니다. 여기서 \*는를 \<*Drive> 설치한 드라이브를 나타내고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<*InstanceName*> 는 인스턴스의 이름입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="de5c6-148">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="de5c6-149">\*\* \<Drive> : Files\Microsoft SQL Server\MSSQL11\*\* **. \<InstanceName> \MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="de5c6-149">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL11** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="de5c6-150">방화벽을 통해 연결하는 경우 방화벽에 원격 대상 컴퓨터의 WMI에 대한 예외가 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="de5c6-150">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="de5c6-151">자세한 내용은 [Windows Vista부터 원격으로 WMI에 연결](https://go.microsoft.com/fwlink/?LinkId=178848)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de5c6-151">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5c6-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de5c6-152">See Also</span></span>  
 <span data-ttu-id="de5c6-153">[SqlErrorLogEvent 클래스](sqlerrorlogevent-class.md) </span><span class="sxs-lookup"><span data-stu-id="de5c6-153">[SqlErrorLogEvent Class](sqlerrorlogevent-class.md) </span></span>  
 [<span data-ttu-id="de5c6-154">오프라인 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="de5c6-154">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
