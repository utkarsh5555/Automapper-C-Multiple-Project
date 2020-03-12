Project Where AutoMapper Is Installed 
 public class AutoMapperStartupTask
 {
        public static MapperConfigurationExpression cfg { get; set; } = new MapperConfigurationExpression();
        public static void Configure()
        {
          cfg.CreateMap<TSource,TDestination>()
          .ForMember(d => d.UserName, opt => opt.MapFrom(src => userName))
          ;
          Mapper.Initialize(cfg);
        }
 }
 
 -----------------------------------------
 Project where above file needs to be inherited.
 
 
public static void Configure()
{
    PARENTPROJECT.AutoMapperStartupTask.cfg.CreateMap<TSource, TDestination>(); 
    PARENTPROJECT.AutoMapperStartupTask.Configure();
}
--------------------------
same Project Global.ASAX
--------------------------
AutoMapperStartupTask.Configure(); 
